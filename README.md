# node-red-contrib-openhab3

## Description

Nodes facilitating the automation of *openHAB* ( <http://www.openhab.org> ) items with Node-RED ( <http://nodered.org> ). This is a fork from Peter De Mangelaere [node-red-contrib-openhab2 package](https://flows.nodered.org/node/node-red-contrib-openhab2) with additions I find useful.

![OpenHAB Node-RED nodes](images/openhab_nodes.png)

## Installation

Install this package `node-red-contrib-openhab3` via the `Manage palette` menu of your Node-RED instance.

## Nodes

See [77-openhab2.html](77-openhab2.html) for info on the provided nodes. This is best viewed from Node-RED, per node.

## Testing the plugin

Prerequisites for running this test environment are docker and docker-compose. It allows you to test this plugin for development purposes.
Docker is used to start a clean Node-RED, OpenHAB v2 and OpenHAB v3 environment, with this plugin installed into Node-RED before the service is started (inside the container).

    # Start by running Node-RED and OpenHAB
    ./run.sh

After a little while, you can visit:

- [Node-RED](http://localhost:1880)
- [OpenHAB v2](http://localhost:8080)
- [OpenHAB v3](http://localhost:8081)

When in the Node-RED UI, you can import [flow.json](test/nodered/flow.json) via the `Import` option, which contains some example tests for each of the nodes, per OpenHAB version, running simultaneously.

You can verify the server sides event connections to be working as well. They are used by the plugin to receive any updates from OpenHAB:

- [OpenHAB 2](http://localhost:8080/rest/events?topics=smarthome/items)
- [OpenHAB 3](http://localhost:8081/rest/events?topics=openhab/items)

When finished, you can reset the test-setup from scratch (this also removes volumes):

    ./clean.sh
