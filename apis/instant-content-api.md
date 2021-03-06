---
description: >-
  A Read Only JSON API to access any content created and managed on the Zesty.io
  Content Platform
---

# Instant Content API

## What is the Zesty.io Instant Content API?

The Instant Content API \(ICA\) is a Read Only interface that returns JSON data via HTTP GET requests. It uses Zesty Unique Identifiers \(ZUID\)s to return information. ICA is primarily used for headless applications, but is not limited to that use. Dynamic Website data or middleware interpreters are also common uses.

This API is intended to be used to retrieve basic information about content in your instance. If you want to receive different file types \(e.g. SVG, XML, RSS, etc\), or submit parameters, we recommend using the Custom JSON API Instead.

## Introduction

### Getting Started

#### Enabling Instant Content API

ICA is an optional feature on every Zesty.io Instance. It can be turned on from the developers settings in the Instances Manager Interface.

#### Accessing Instant Content API Endpoints

To access ICA, you make a call to your preview URL or live domain, for example: [http://burger.zesty.site/-/instant/6-4b5c74-fg83s2.json](http://burger.zesty.site/-/instant/6-4b5c74-fg83s2.json). Swap out the domain for your preview URL or your live domain. Switch out the HASH for a resource you wish to access on your Zesty.io instance.

The hash you see is a ZUID. ZUIDs are used to represent every type of resource in Zesty.io. You can find the ZUID of a resource in a few ways through the Zesty.io Content Manager. When editing content, you will see the ZUID \(items start with 7-\) of that content in the URL of the page you are editing. You can access model ZUIDS \(models start with 6-\) by looking in the schema \(previously config\) tab.

When you visit the BAC URL you see a JSON object of the data associated with the resource you are requesting along with meta data, version information, image objects, and related resources objects.

* TODO - ADD SCREENSHOTS SHOWING WHERE API ENDPOINT URLS ARE SHOWN IN THE MANAGER
  * do this through github
* TODO - ADD EXAMPLE JSON RESPONSE

## Security

ICA is optional and has to be turned on to gain access to it. Options to control Cross Origin Resource Sharing can be used to lock the API down to specific websites. A header request with a private token can be set to secure external programmatic application calls.

## JSON Format

{% api-method method="get" host="https://yoursite.com" path="/-/instant/zuid.json" %}
{% api-method-summary %}
General Format
{% endapi-method-summary %}

{% api-method-description %}
All objects will return meta and data fields.The meta field gives information on what type the object is, in addition to its model container.The data field contains meta, version, and content fields.The data meta field contains the actual object metadata, the data version field contains information detailing which version was returned. Lastly, the data content field returns the actual content that was set in the config tab of Zesty.io
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Access Token" type="string" required=false %}
Name and value may change in the future. You can also  
configure your site to not need this
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned if the zuid exists \(Generic Item Example\)
{% endapi-method-response-example-description %}

{% code-tabs %}
{% code-tabs-item title="response.json" %}
```yaml
{
    "meta": {
        "type": "item",
        "zuid": "your-zuid",
        "createdAt": "2018-07-10 23:03:25",
        "totalItems": 1,
        "listed": 1,
        "model": {
            "type": "model",
            "zuid": "6-model-zuid",
            "name": "some model",
            "label": "Some Model",
            "resourceURI": "\/-\/instant\/6-model-zuid.json"
        },
        "web": {
            "uri": "\/",
            "fragment": "zesty_home"
        }
    },
    "data": [
    {
        "meta": {
            "type": "item",
            "zuid": "7-4ad498-k2cldb",
            "name": "Homepage",
            "title": "Homepage",
            "description": "Some Description",
            "keywords": "key, words",
            "language": 1,
            "model": {
                "type": "model",
                "zuid": "6-model-zuid",
                "name": "some model",
                "label": "Some Model",
                "resourceURI": "\/-\/instant\/6-model-zuid.json"
            },
            "parent": {
                "type": "abstract",
                "zuid": "7-parent-item-zuid",
                "resourceURI": "\/-\/instant\/7-parent-item-zuid.json",
            }
        },
        "version": {
            "zuid": "9-version-zuid",
            "createdAt": "2018-08-17 22:49:06",
            "iteration": 15,
            "history": {
                "type": "versions",
                "totalItems": 0,
                "data": null
            }
        },
        "content": {
            "refName" : "value",
            "zuid": "18-content-zuid",
            "version_zuid": "9-6d2c2e2-dlhtq6",
            "version_num": 15,
            "publish_at": "2018-08-17 22:49:07",
            "take_offline_at": null
        }
    }]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://yoursite.com" path="/-/instant/7-item-zuid.json" %}
{% api-method-summary %}
Content Items
{% endapi-method-summary %}

{% api-method-description %}
Content Items are designated by a 7 in their zuid. Items will only return one object in the data array.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Access Token" type="string" required=false %}
Name and value may change in the future. You can also  
configure your site to not need this
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned if the zuid exists \(Generic Item Example\)
{% endapi-method-response-example-description %}

{% code-tabs %}
{% code-tabs-item title="response.json" %}
```yaml
{
    "meta": {
        "type": "item",
        "zuid": "your-zuid",
        "createdAt": "2018-07-10 23:03:25",
        "totalItems": 1,
        "listed": 1,
        "model": {
            "type": "model",
            "zuid": "6-model-zuid",
            "name": "some model",
            "label": "Some Model",
            "resourceURI": "\/-\/instant\/6-model-zuid.json"
        },
        "web": {
            "uri": "\/",
            "fragment": "zesty_home"
        }
    },
    "data": [
    {
        "meta": {
            "type": "item",
            "zuid": "7-4ad498-k2cldb",
            "name": "Homepage",
            "title": "Homepage",
            "description": "Some Description",
            "keywords": "key, words",
            "language": 1,
            "model": {
                "type": "model",
                "zuid": "6-model-zuid",
                "name": "some model",
                "label": "Some Model",
                "resourceURI": "\/-\/instant\/6-model-zuid.json"
            },
            "parent": {
                "type": "abstract",
                "zuid": "7-parent-item-zuid",
                "resourceURI": "\/-\/instant\/7-parent-item-zuid.json",
            }
        },
        "version": {
            "zuid": "9-version-zuid",
            "createdAt": "2018-08-17 22:49:06",
            "iteration": 15,
            "history": {
                "type": "versions",
                "totalItems": 0,
                "data": null
            }
        },
        "content": {
            "refName" : "value",
            "zuid": "18-content-zuid",
            "version_zuid": "9-6d2c2e2-dlhtq6",
            "version_num": 15,
            "publish_at": "2018-08-17 22:49:07",
            "take_offline_at": null
        }
    }]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://yoursite.com" path="/-/instant/6-array-zuid.json" %}
{% api-method-summary %}
Models \(Previously known as Pagesets, Templatesets, Datasets\)
{% endapi-method-summary %}

{% api-method-description %}
Arrays are designated by a 6 in their zuid. They can return multiple items.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Access Token" type="string" required=false %}
Name and value may change in the future. You can also  
configure your site to not need this
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned if the zuid exists \(Generic Item Example\)
{% endapi-method-response-example-description %}

{% code-tabs %}
{% code-tabs-item title="response.json" %}
```yaml
{
    "meta": {
        "type": "model",
        "zuid": "6-zuid",
        "createdAt": "2018-07-10 23:17:27",
        "model": {
            "type": "model",
            "zuid": "6-model-zuid",
            "name": "location_pages",
            "label": "Some Model",
            "resourceURI": "\/-\/instant\/6-model-zuid.json"
        },
        "totalItems": 2
    },
    "data": [
        {
            "meta": {
                "type": "item",
                "zuid": "7-zuid",
                "name": "Some Item",
                "title": "Some Item",
                "description": "some description",
                "keywords": "key, words",
                "language": 1,
                "model": {
                    "type": "model",
                    "zuid": "6-model-zuid",
                    "name": "location_pages",
                    "label": "Some Model",
                    "resourceURI": "\/-\/instant\/6-model-zuid.json"
                },
                "parent": {
                    "type": "item",
                    "zuid": "7-parent-zuid",
                    "resourceURI": "\/-\/instant\/7-parent-zuid.json"
                }
            },
            "version": {
                "zuid": "9-version-zuid",
                "createdAt": "2018-07-25 23:05:29",
                "iteration": 19,
                "history": {
                    "type": "versions",
                    "totalItems": 0,
                    "data": null
                }
            },
            "content": {
                "sort": 1,
                "some_property": "Value",
                "zuid": "18-content-zuid",
                "item_zuid": {
                    "type": "relationship",
                    "totalItems": 1,
                    "data": [{
                        "type": "item",
                        "zuid": "7-item-zuid",
                        "resourceURI": "\/-\/instant\/7-item-zuid.json"
                    }]
                },
                "version_zuid": "9-version-zuid",
                "version_num": 19,
                "publish_at": "2018-07-25 23:05:30",
                "take_offline_at": null
            }
        },
        { ... }        
    ]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Datatypes Returned

### Images

Images are returned as objects, containing data regarding how many images were returned, as well as the media url and the image zuid

```text
"imageRef" : {
    "type": "images",
    "totalItems": 2,
    "data": [
        {
            "type": "image",
            "zuid": "3-image-zuid",
            "url": "https:\/\/instance.media.zestyio.com\/path\/to\/.jpg"
        },
        {
            "type": "image",
            "zuid": "3-image-zuid",
            "url": "https:\/\/instance.media.zestyio.com\/path\/to\/.jpg"
        }
    ]
}
```

### Relationships

Relationships \(such as `one-to-one` and `one-to-many`\) are returned as objects, containing data regarding how many items are related \(`one-to-one` relationships will always return 1\) , as well as a resource URI to retrieve more data on the related item

```text
"relationshipRef": {
    "type": "relationship",
    "totalItems": 2,
    "data": [
        {
            "type": "item",
            "zuid": "7-zuid",
            "resourceURI": "\/-\/instant\/7-zuid.json"
        },
        {
            "type": "item",
            "zuid": "7-zuid",
            "resourceURI": "\/-\/instant\/7-zuid.json"
        }
    ]
},
```

