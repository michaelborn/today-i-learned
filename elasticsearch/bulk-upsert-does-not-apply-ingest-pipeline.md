# Elasticsearch Bulk Upsert Does Not Apply the Default Ingest Pipeline To Existing Documents

I was today-years-old when I learned that ElasticSearch will not apply an ingest pipeline to existing documents during a bulk upsert operation.

As a quick example, consider the following bulk upsert request:

```sh
POST my-index/_bulk
{"update":{"_id":"123"}}
{"doc":{"status":"active","count":1},"doc_as_upsert":true}
```

I ran into an issue where a pre-existing document was retaining field values after bulk index which should removed by the default pipeline.

I asked Perplexity about this, and I got this response:

> Yes—Bulk API upserts can use an index’s index.default_pipeline when the upsert results in a new document being created, provided you do not override the pipeline at request or per-item level. Existing-document updates are not generally re-ingested through the default pipeline.
> 
> ...
>  
> If [the document] already exists, Elasticsearch applies the partial update and does not run the ingest pipeline over the merged stored document.

This feels a bit "wrong" to me, instinctually, just because I would expect an ingest pipeline to allow transformations to be applied consistently, whether creating NEW documents or merely updating existing ones.

However...they are called *ingest* pipelines for a reason! And you can still [apply pipelines manually](#manually-applying-a-pipeline-during-bulk-insert). Lessons learned!

## Manually Applying a Pipeline During Bulk Insert

One easy fix is to manually specify the pipeline as a `?pipeline=my-pipeline` query parameter in your indexing requests:

```sh
POST my-data-stream/_doc?pipeline=my-pipeline
{
  "@timestamp": "2099-03-07T11:04:05.000Z",
  "my-keyword-field": "foo"
}
PUT my-data-stream/_bulk?pipeline=my-pipeline
{ "create":{ } }
{ "@timestamp": "2099-03-07T11:04:06.000Z", "my-keyword-field": "foo" }
{ "create":{ } }
{ "@timestamp": "2099-03-07T11:04:07.000Z", "my-keyword-field": "bar" }
```

[See ES documentation for more details](https://www.elastic.co/docs/manage-data/ingest/transform-enrich/ingest-pipelines#add-pipeline-to-indexing-request).