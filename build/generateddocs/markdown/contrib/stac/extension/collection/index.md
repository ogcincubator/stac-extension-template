
# STAC Collection (Schema)

`ogc.contrib.stac.extension.collection` *v0.1*

Replace with description of your extension

[*Status*](http://www.opengis.net/def/status): Under development

## Examples

### STAC extension template collection
This is the default stac-extension template example. Replace with an example of your extension.

#### json
```json
{
  "stac_version": "1.0.0",
  "stac_extensions": [
    "https://stac-extensions.github.io/item-assets/v1.0.0/schema.json",
    "https://stac-extensions.github.io/template/v1.0.0/schema.json"
  ],
  "type": "Collection",
  "id": "collection",
  "title": "A title",
  "description": "A description",
  "license": "Apache-2.0",
  "extent": {
    "spatial": {
      "bbox": [
        [
          172.9,
          1.3,
          173,
          1.4
        ]
      ]
    },
    "temporal": {
      "interval": [
        [
          "2015-06-23T00:00:00Z",
          null
        ]
      ]
    }
  },
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
  ],
  "assets": {
    "example": {
      "href": "https://example.com/examples/file.xyz",
      "template:new_field": "test"
    }
  },
  "item_assets": {
    "data": {
      "roles": [
        "data"
      ],
      "template:new_field": "test"
    }
  },
  "summaries": {
    "datetime": {
      "minimum": "2015-06-23T00:00:00Z",
      "maximum": "2019-07-10T13:44:56Z"
    }
  },
  "links": [
    {
      "href": "https://example.com/examples/collection.json",
      "rel": "self"
    },
    {
      "href": "https://example.com/examples/item.json",
      "rel": "item"
    }
  ]
}

```

#### jsonld
```jsonld
{
  "stac_version": "1.0.0",
  "stac_extensions": [
    "https://stac-extensions.github.io/item-assets/v1.0.0/schema.json",
    "https://stac-extensions.github.io/template/v1.0.0/schema.json"
  ],
  "type": "Collection",
  "id": "collection",
  "title": "A title",
  "description": "A description",
  "license": "Apache-2.0",
  "extent": {
    "spatial": {
      "bbox": [
        [
          172.9,
          1.3,
          173,
          1.4
        ]
      ]
    },
    "temporal": {
      "interval": [
        [
          "2015-06-23T00:00:00Z",
          null
        ]
      ]
    }
  },
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
  ],
  "assets": {
    "example": {
      "href": "https://example.com/examples/file.xyz",
      "template:new_field": "test"
    }
  },
  "item_assets": {
    "data": {
      "roles": [
        "data"
      ],
      "template:new_field": "test"
    }
  },
  "summaries": {
    "datetime": {
      "minimum": "2015-06-23T00:00:00Z",
      "maximum": "2019-07-10T13:44:56Z"
    }
  },
  "links": [
    {
      "href": "https://example.com/examples/collection.json",
      "rel": "self"
    },
    {
      "href": "https://example.com/examples/item.json",
      "rel": "item"
    }
  ],
  "@context": "https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/context.jsonld"
}
```

#### ttl
```ttl
@prefix dcterms: <http://purl.org/dc/terms/> .
@prefix ns1: <template:> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

[] rdfs:label "A title" ;
    dcterms:type "Collection" ;
    ns1:another_one 1,
        2,
        3 ;
    ns1:new_field "test" ;
    ns1:xyz [ ] .


```

## Schema

```yaml
$schema: http://json-schema.org/draft-07/schema#
$id: https://stac-extensions.github.io/template/v1.0.0/schema.json#
title: Template Extension
description: STAC Template Extension for STAC Items and STAC Collections, using the
  base STAC schemas via building block references
oneOf:
- $comment: This is the schema for STAC Collections.
  type: object
  allOf:
  - $ref: https://ogcincubator.github.io/bblocks-stac/build/annotated/contrib/stac/collection/schema.yaml
  - $ref: '#/definitions/stac_extensions'
  anyOf:
  - $comment: This is the schema for the top-level fields in a Collection. Remove
      this if this extension does not define top-level fields for Collections.
    allOf:
    - $comment: Require fields here for Collections (top-level).
      required:
      - template:new_field
    - $ref: '#/definitions/fields'
  - $comment: This validates the fields in Collection Assets, but does not require
      them.
    required:
    - assets
    properties:
      assets:
        type: object
        not:
          additionalProperties:
            not:
              allOf:
              - $ref: '#/definitions/require_any_field'
              - $ref: '#/definitions/fields'
  - $comment: This is the schema for the fields in Item Asset Definitions. It doesn't
      require any fields.
    required:
    - item_assets
    properties:
      item_assets:
        type: object
        not:
          additionalProperties:
            not:
              allOf:
              - $ref: '#/definitions/require_any_field'
              - $ref: '#/definitions/fields'
  - $comment: This is the schema for the fields in Summaries. By default, only checks
      the existence of the properties, but not the schema of the summaries.
    required:
    - summaries
    properties:
      summaries:
        $ref: '#/definitions/require_any_field'
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

```

Links to the schema:

* YAML version: [schema.yaml](https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/schema.json)
* JSON version: [schema.json](https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
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
    "type": "dct:type",
    "hreflang": "dct:language",
    "title": "rdfs:label",
    "length": "dct:extent",
    "oa": "http://www.w3.org/ns/oa#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "dct": "http://purl.org/dc/terms/",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/context.jsonld)

## Sources

* [STAC Specification](https://stacspec.org/en/about/stac-spec/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/ogcincubator/stac-extension-template](https://github.com/ogcincubator/stac-extension-template)
* Path: `_sources/collection`

