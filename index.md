
# User guide

This guide serves as some notes as to how this application should be used. Its usage is explained and its limitations are mentioned.

## Defining a test plan

The user defines the test plan as a tree. A service instance is modelled by a node. An edge contains the needed test parameters.  These test parameters are messages. One could think of an edge as sending a message to the target of the edge. The root of the tree should always be a node with the text "Start". The edges connected to the Start-node will be the starting point of the tree traversal.
A Start-node should always be added to the diagram. The user should drag and drop this Start-node on the diagram on the diagram in the middle. 
Then, the user chooses one of the available services in the left panel to construct a tree.

For each edge, the user can specify some fields. These are the parameters that will be used for the test.
Which fields are available depends on wether the edge is connected to the root.
If the edge is connected to the root, the user specifies the input message that will be sent to the target node of the edge. One could think of this message as a 'seed' for the other edges in the branch connected to this edge.
The service will process this message and possibly send an output message. The messages 'propagate' through the branch of the tree.

If the edge is connected to the root, the following fields can be specified:
* An input message, that will be sended to the target of the edge
* The expected output of the service, after sending the said input message to the service. Note that the user can also specify an empty message, if the user assumes that no output is expected from the service.

If the edge is not connected to the root, the following fields can be specified:
* An expected input message. 
* An expected message. This has the same meaning as in the case where the edge is connected to the root.


## Executing a test plan

After a test plan is specified, the user should click on the 'Send'-button. After some moments, the edges are colored green or red. If the edge is green, this means that all executed checks for this edge were succesfull. If the edge is red, this means that a failure happened. Doubleclicking an edge will show a pop-up with feedback about the results, e.g. what element in the test failed. The user can close the pop-up by clicking in the space around the pop-up.

Tests can be rerun and associated field to edges can be modified.
It is possible to save a test plan and the feedback in JSON-files.

## Simulating the tree traversal

To help the user with organizing the tests, the user can simulate the traversal by clicking on the button 'Show traverse order'. After some moments, each edge is labeled with a number that represents the order in which the edge will be traversed.

## Example


## Limitations

* The test plan must be a tree, i.e. a directed acyclic graph. So loops from nodes to themselves, edges between two branches etc. are not allowed.

* It is possible that a service reacts on the output of some service that is not specified by the test tree. Only the services specified in the graph are taken into account in the test.
