# ElasticSearch PHP client
ElasticSearch is a distributed lucene powered search indexing, this is a PHP client for it
## Warning: API WILL CHANGE
## Basic usage
    require_once "ElasticSearchClient.php";
    $transport = new ElasticSearchTransportHTTP("localhost", 9200);
    $search = new ElasticSearchClient($transport, "myindex", "mytype");
    $search->index(array('title' => 'My cool document'), $id);
    $search->get($id);
    $search->search('title:cool');

## Multiple indexes or types
    $search->setIndex(array("one", "two"));
    $search->setType(array("mytype", "other-type"));
    $search->search('title:cool');

## Using the Query DSL
    $search->search(array(
        'query' => array(
            'term' => array('title' => 'cool')
        )
    );
