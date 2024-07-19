
# STAC Item - Extension Template (Schema)

`ogc.contrib.stac.extension.item` *v0.1*

Replace with description of your extension

[*Status*](http://www.opengis.net/def/status): Under development

## Examples

### STAC extension template item example
This is the default stac-extension template example. Replace with an example of your extension. 

#### json
```json
{
  "stac_version": "1.0.0",
  "stac_extensions": [
    "https://stac-extensions.github.io/template/v1.0.0/schema.json"
  ],
  "type": "Feature",
  "id": "item",
  "bbox": [
    172.9,
    1.3,
    173,
    1.4
  ],
  "geometry": {
    "type": "Polygon",
    "coordinates": [
      [
        [
          172.9,
          1.3
        ],
        [
          173,
          1.3
        ],
        [
          173,
          1.4
        ],
        [
          172.9,
          1.4
        ],
        [
          172.9,
          1.3
        ]
      ]
    ]
  },
  "properties": {
    "datetime": "2020-12-11T22:38:32Z",
    "template:new_field": "test",
    "template:xyz": {
      "x": 1,
      "y": 2,
      "z": 3
    },
    "template:another_one": [
      1,
      2,
      3
    ]
  },
  "links": [
    {
      "href": "https://example.com/examples/item.json",
      "rel": "self"
    }
  ],
  "assets": {
    "data": {
      "href": "https://example.com/examples/file.xyz",
      "template:new_field": "test"
    }
  }
}

```

#### jsonld
```jsonld
{
  "stac_version": "1.0.0",
  "stac_extensions": [
    "https://stac-extensions.github.io/template/v1.0.0/schema.json"
  ],
  "type": "Feature",
  "id": "item",
  "bbox": [
    172.9,
    1.3,
    173,
    1.4
  ],
  "geometry": {
    "type": "Polygon",
    "coordinates": [
      [
        [
          172.9,
          1.3
        ],
        [
          173,
          1.3
        ],
        [
          173,
          1.4
        ],
        [
          172.9,
          1.4
        ],
        [
          172.9,
          1.3
        ]
      ]
    ]
  },
  "properties": {
    "datetime": "2020-12-11T22:38:32Z",
    "template:new_field": "test",
    "template:xyz": {
      "x": 1,
      "y": 2,
      "z": 3
    },
    "template:another_one": [
      1,
      2,
      3
    ]
  },
  "links": [
    {
      "href": "https://example.com/examples/item.json",
      "rel": "self"
    }
  ],
  "assets": {
    "data": {
      "href": "https://example.com/examples/file.xyz",
      "template:new_field": "test"
    }
  },
  "@context": "https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/item/context.jsonld"
}
```

#### ttl
```ttl
@prefix geojson: <https://purl.org/geojson/vocab#> .
@prefix ns1: <template:> .
@prefix ns2: <http://www.iana.org/assignments/> .
@prefix oa: <http://www.w3.org/ns/oa#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix stac: <https://w3id.org/ogc/stac/core/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://example.com/stac/example1/item> a geojson:Feature ;
    rdfs:seeAlso [ ns2:relation <http://www.iana.org/assignments/relation/self> ;
            oa:hasTarget <https://example.com/examples/item.json> ] ;
    geojson:bbox ( 1.729e+02 1.3e+00 173 1.4e+00 ) ;
    geojson:geometry [ a geojson:Polygon ;
            geojson:coordinates ( ( ( 1.729e+02 1.3e+00 ) ( 173 1.3e+00 ) ( 173 1.4e+00 ) ( 1.729e+02 1.4e+00 ) ( 1.729e+02 1.3e+00 ) ) ) ] ;
    stac:assets <https://example.com/stac/example1/data> ;
    ns1:another_one 1,
        2,
        3 ;
    ns1:new_field "test" ;
    ns1:xyz [ ] .

<https://example.com/stac/example1/data> oa:hasTarget <https://example.com/examples/file.xyz> ;
    ns1:new_field "test" .


```

## Schema

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://stac-extensions.github.io/template/v1.0.0/schema.json#
title: Template Extension
description: STAC Template Extension for STAC Items and STAC Collections, using the
  base STAC schemas via building block references
oneOf:
- $comment: This is the schema for STAC Items. Remove this object if this extension
    only applies to Collections.
  allOf:
  - $ref: https://ogcincubator.github.io/bblocks-stac/build/annotated/contrib/stac/item/schema.yaml
  - $ref: '#/definitions/stac_extensions'
  - type: object
    properties:
      properties:
        allOf:
        - $comment: Require fields here for Item Properties.
          required:
          - template:new_field
        - $ref: '#/definitions/fields'
      assets:
        $comment: This validates the fields in Item Assets, but does not require them.
        type: object
        additionalProperties:
          $ref: '#/definitions/fields'
        x-jsonld-id: https://w3id.org/ogc/stac/core/assets
        x-jsonld-container: '@id'
definitions:
  stac_extensions:
    type: object
    required:
    - stac_extensions
    properties:
      stac_extensions:
        type: array
        contains:
          const: https://stac-extensions.github.io/template/v1.0.0/schema.json
  require_any_field:
    $comment: Please list all fields here so that we can force the existence of one
      of them in other parts of the schemas.
    anyOf:
    - required:
      - template:new_field
    - required:
      - template:xyz
    - required:
      - template:another_one
  fields:
    $comment: Add your new fields here. Don't require them here, do that above in
      the corresponding schema.
    type: object
    properties:
      template:new_field:
        type: string
      template:xyz:
        type: object
        required:
        - x
        - y
        - z
        properties:
          x:
            type: number
          y:
            type: number
          z:
            type: number
      template:another_one:
        type: array
        items:
          type: number
    patternProperties:
      ^(?!template:):
        $comment: Above, change `template` to the prefix of this extension
    additionalProperties: false
x-jsonld-prefixes:
  stac: https://w3id.org/ogc/stac/core/

```

Links to the schema:

* YAML version: [schema.yaml](https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/item/schema.json)
* JSON version: [schema.json](https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/item/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "type": "@type",
    "id": "@id",
    "properties": "@nest",
    "geometry": {
      "@context": {},
      "@id": "geojson:geometry"
    },
    "bbox": {
      "@container": "@list",
      "@id": "geojson:bbox"
    },
    "Feature": "geojson:Feature",
    "FeatureCollection": "geojson:FeatureCollection",
    "GeometryCollection": "geojson:GeometryCollection",
    "LineString": "geojson:LineString",
    "MultiLineString": "geojson:MultiLineString",
    "MultiPoint": "geojson:MultiPoint",
    "MultiPolygon": "geojson:MultiPolygon",
    "Point": "geojson:Point",
    "Polygon": "geojson:Polygon",
    "features": {
      "@container": "@set",
      "@id": "geojson:features"
    },
    "links": {
      "@context": {
        "type": "dct:type"
      },
      "@id": "rdfs:seeAlso"
    },
    "coordinates": {
      "@container": "@list",
      "@id": "geojson:coordinates"
    },
    "href": {
      "@type": "@id",
      "@id": "oa:hasTarget"
    },
    "rel": {
      "@context": {
        "@base": "http://www.iana.org/assignments/relation/"
      },
      "@id": "http://www.iana.org/assignments/relation",
      "@type": "@id"
    },
    "hreflang": "dct:language",
    "title": "rdfs:label",
    "length": "dct:extent",
    "created": "dct:created",
    "updated": "dct:modified",
    "uriTemplate": {
      "@type": "xsd:string",
      "@id": "oa:hasTarget"
    },
    "assets": {
      "@id": "stac:assets",
      "@container": "@id"
    },
    "geojson": "https://purl.org/geojson/vocab#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "oa": "http://www.w3.org/ns/oa#",
    "dct": "http://purl.org/dc/terms/",
    "stac": "https://w3id.org/ogc/stac/core/",
    "xsd": "http://www.w3.org/2001/XMLSchema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/item/context.jsonld)

## Sources

* [STAC Specification](https://stacspec.org/en/about/stac-spec/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/stac-extension-template](https://github.com/ogcincubator/stac-extension-template)
* Path: `_sources/item`

