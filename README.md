# Hyperboria-Map
[![Build Status](https://api.travis-ci.org/waaghals/Hyperboria-Map.png)](https://api.travis-ci.org/waaghals/Hyperboria-Map)

A map of physical Cjdns nodes available for direct peering.

## Why?

To give people a simple place to find local peers.
No more waiting for people to respond on IRC who are close.
Simply pick one of the closest and ask them directly.

## Can I add my node

Only if you are willing to peer with others not using tunneling or are currently peered with atleast on node not using tunneling.

## How can I add my node
Simply fork this repo and add your node information to the `hyperboria.geo.json` file.
The content of this file is [GeoJson](http://geojson.org/geojson-spec.html).
For full instruction see section __Instructions__

### Type of nodes
There are currently three type of nodes.
* Exchange
* Access
* Services

#### Exchange
These node only provide a peering medium. 
This could be Wifi-repeater or a common switch to which other node connect and peer over.
Such a node won't be able to talk the [Cjdns](https://github.com/cjdelisle/cjdns) protocol on its own and needs node connected to it.
It is recommended to keep these nodes in a high desity node location such as a datacenter or a densely populated area.
A example of a Hyperboria Exchange is NL-HX. It is able to connect to any node at [any datacenter that is connected](/nl-ix.geo.json) by the [NL-IX](http://www.nl-ix.net/).

#### Access
These nodes provide a connection to the complete Hyperboria network.
Connecting to at least one of these nodes will provide you with complete access to Hyperboria.
This can be any box with Cjdns on it.

#### Services
These nodes provide a service on Hyperboria. This can be any [service](https://wiki.projectmeshnet.org/Known_Hyperboria_sites) such as a website, irc or Minecraft servers.
A service node on this map needs to have atleast one direct upstream peer.


##Instructions
Open the `hyperboria.geo.json` file in your favorite (json) editor.
Add a `Point` to it using the GeoJson syntax.
If the node is already directly peered with a other node you can add a `LineString` between them.

### Properties
The following properties are mandatory. 
* __type__ _(Either Exchange, Access or Services)_
* __marker-size__ _(Small for services, medium for Access and large for Exchanges.)_
* __connection__ _(Type of connection medium)_
* __maintainer__ _(IRC name)_

Recommended properties
* __marker-color__ _(Identify all your nodes with a common color in RGB hex.)_

Please refrain from using any of the following properties
* __marker-symbol__

### Example code
```json
[
    {
      "type": "Feature",
      "properties": {
        "marker-size": "small",
        "marker-color": "#7a22ad",
        "type": "Services",
        "connection": "Ethernet",
        "maintainer": "Waaghals"
      },
      "geometry": {
        "type": "Point",
        "coordinates": [
          5.93393,
          51.9869
        ]
      }
    },
    {
      "type": "Feature",
      "geometry": {
        "type": "LineString",
        "coordinates": [
          [
            5.934084,
          51.987035
          ],
          [
            5.93393,
          51.98713
          ]
        ]
      }
    }
]
```
