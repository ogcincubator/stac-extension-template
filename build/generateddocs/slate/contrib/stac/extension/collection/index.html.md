---
title: STAC Collection (Schema)

language_tabs:
  - json: JSON
  - jsonld: JSON-LD
  - turtle: RDF/Turtle

toc_footers:
  - Version 0.1
  - <a href='#'>STAC Collection</a>
  - <a href='https://blocks.ogc.org/register.html'>Building Blocks register</a>

search: true

code_clipboard: true

meta:
  - name: STAC Collection (Schema)
---


# STAC Collection `ogc.contrib.stac.extension.collection`

Replace with description of your extension

<p class="status">
    <span data-rainbow-uri="http://www.opengis.net/def/status">Status</span>:
    <a href="http://www.opengis.net/def/status/under-development" target="_blank" data-rainbow-uri>Under development</a>
</p>

<aside class="success">
This building block is <strong><a href="https://github.com/ogcincubator/stac-extension-template/blob/main/build/tests/contrib/stac/extension/collection/" target="_blank">valid</a></strong>
</aside>

# Examples

## STAC extension template collection



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

<blockquote class="lang-specific json">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/tests/contrib/stac/extension/collection/example_1_1.json">Open in new window</a>
    <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=json&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fstac-extension-template%2Fmain%2Fbuild%2Ftests%2Fcontrib%2Fstac%2Fextension%2Fcollection%2Fexample_1_1.json&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on JSON Viewer</a></p>
</blockquote>




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

<blockquote class="lang-specific jsonld">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/tests/contrib/stac/extension/collection/example_1_1.jsonld">Open in new window</a>
    <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fstac-extension-template%2Fmain%2Fbuild%2Ftests%2Fcontrib%2Fstac%2Fextension%2Fcollection%2Fexample_1_1.jsonld">View on JSON-LD Playground</a>
</blockquote>




```turtle
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

<blockquote class="lang-specific turtle">
  <p class="example-links">
    <a target="_blank" href="https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/tests/contrib/stac/extension/collection/example_1_1.ttl">Open in new window</a>
</blockquote>


This is the default stac-extension template example. Replace with an example of your extension.



# JSON Schema

```yaml--schema
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

> <a target="_blank" href="https://avillar.github.io/TreedocViewer/?dataParser=yaml&amp;dataUrl=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fstac-extension-template%2Fmain%2Fbuild%2Fannotated%2Fcontrib%2Fstac%2Fextension%2Fcollection%2Fschema.yaml&amp;expand=2&amp;option=%7B%22showTable%22%3A+false%7D">View on YAML Viewer</a>

Links to the schema:

* YAML version: <a href="https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/schema.yaml" target="_blank">https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/schema.yaml</a>
* JSON version: <a href="https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/schema.json" target="_blank">https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/schema.json</a>


# JSON-LD Context

```json--ldContext
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

> <a target="_blank" href="https://json-ld.org/playground/#json-ld=https%3A%2F%2Fraw.githubusercontent.com%2Fogcincubator%2Fstac-extension-template%2Fmain%2Fbuild%2Fannotated%2Fcontrib%2Fstac%2Fextension%2Fcollection%2Fcontext.jsonld">View on JSON-LD Playground</a>

You can find the full JSON-LD context here:
<a href="https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/context.jsonld" target="_blank">https://raw.githubusercontent.com/ogcincubator/stac-extension-template/main/build/annotated/contrib/stac/extension/collection/context.jsonld</a>

# References

* [STAC Specification](https://stacspec.org/en/about/stac-spec/)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: <a href="https://github.com/ogcincubator/stac-extension-template" target="_blank">https://github.com/ogcincubator/stac-extension-template</a>
* Path:
<code><a href="https://github.com/ogcincubator/stac-extension-template/blob/HEAD/_sources/collection" target="_blank">_sources/collection</a></code>

