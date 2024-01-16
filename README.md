# Salesforce-BatchIt
A simple but extremely useful batching tool.

Instead of writing a new batchable Apex class every time you want to insert or update some SObject records in a batch, you can just send the collection to this, and it takes care of the batching for you.

## Usage:

  Database.executeBatch(new BatchIt(\<SObject List\>, <'insert', 'update', or 'upsert'>, [optional all_or_nothing Boolean]), [optional batch size Integer]);

## Example:
  In most cases, you'll probably want to use the quick version (which upserts):
  
    BatchIt.now(some_sobject_list_of_records);

or

    BatchIt.now(some_sobject_list_of_records, batch_size);

... but if you want or need to specify the action instead of defaulting to upsert, you can declare it and, optionally, provide an "All or Nothing" value.

This example also provides an optional batch size which is a standard option of the Database.executeBatch() method.
  
    Database.executeBatch(new BatchIt(some_sobject_list_of_records, 'insert', true), 10);
