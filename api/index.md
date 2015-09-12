# Lime API Documentation
The REST API through which the Lime frontend communicates with the backend.

All endpoints are prefixed with `/api/v1/`.

* [Body](#body)
  * [`GET /body/`](#get-the-body)
* [Happenings](#happenings)
  * [`GET /happenings/`](#get-happenings)
* [Host](#host)
  * [`GET /host/`](#get-host)
* [Vertex](#vertex)
  * [`GET /<vertex_type>/`](#get-all-vertices)
  * [`POST /<vertex_type>/`](#create-a-new-vertex)
  * [`GET /<vertex_type>/<id>`](#get-a-specific-vertex)
  * [`PUT /<vertex_type>/<id>`](#update-a-specific-vertex)
  * [`DELETE /<vertex_type>/<id>`](#delete-a-vertex)
  * [`GET /<vertex_type>/form/`](#get-vertex-form)
* [Edge](#edge)
  * [`POST /edge/`](#create-edge)
  * [`DELETE /edge/`](#delete-edge)
* ~~[Deprecated](#soon-to-be-deprecated-endpoints)~~
  * ~~[`GET /photo/`](#get-photo)~~
  * ~~[`GET /audio/`](#get-audio)~~
  * ~~[`GET /user/`](#get-user)~~
  * ~~[`PUT /<vertex_type>/<id>/succset/`](##put-vertex-succset)~~

## Body
### Get the body
* **Description:** Gets the body apex of the current user.
* **Definition:** `GET /body/`
* **Example:**c
```json
GET /body/
{
  "result": {
    "_cls": "Vertex.Apex.Body",
    "_id": <vertex_id>,
    "cover": [],
    "deletable": true,
    "host": <host_id>,
    "layout": "",
    "public": true,
    "predset": [],
    "slug": "www-wiota-co",
    "source": true,
    "succset": [
        <list_of_vertices>
    ],
    "title": "www.wiota.co",
    "vertex_type": "body"
  }
}
```

## Happenings
### Get happenings
* **Description:** Gets the happenings apex of the current user.
* **Definition:** `GET /happenings/`
* **Example:**
```json
GET /happenings/
{
  "result": {
    "_cls": "Vertex.Apex.Happenings",
    "_id": <vertex_id>,
    "deletable": true,
    "cover": [],
    "host": <host_id>,
    "layout": "",
    "public": true,
    "predset": [],
    "slug": "happenings",
    "source": true,
    "succset": [
        <list_of_happenings>
    ],
    "title": "happenings",
    "vertex_type": "calendar"
  }
}
```

## Host
### Get host
* **Description:** Gets the host of the current user.
* **Definition:** `GET /host/`
* **Example:**
```json
GET /host/
{
  "result": {
    "_id": <vertex_id>,
    "apex": {
      "host": <host_id>,
      "title": "wiota.co",
      "deletable": false,
      "_id": <vertex_id>,
      "vertex_type": "host",
      "source": true,
      "slug": "wiota-co",
      "layout": "",
      "succset": [
        <list_of_vertices>
      ],
      "predset": [],
      "_cls": "Vertex.Apex",
      "public": true,
      "cover": []
    },
    "bucketname": <bucket_name>,
    "custom_pages": [],
    "custom_vertex_fields": {
      "text": [
        {
          "required": false,
          "field_type": "StringField",
          "name": "title",
          "_cls": "CustomVertexField",
          "verbose_name": "Title"
        },
        {
          "required": false,
          "field_type": "LongStringField",
          "name": "text",
          "_cls": "CustomVertexField",
          "verbose_name": "Text"
        }
      ],
      "category": [
        {
          "required": false,
          "field_type": "StringField",
          "name": "title",
          "_cls": "CustomVertexField",
          "verbose_name": "Title"
        },
        {
          "required": false,
          "field_type": "LongStringField",
          "name": "description",
          "_cls": "CustomVertexField",
          "verbose_name": "Description"
        }
      ]
    },
    "hostname": "wiota.co",
    "owners": [
        <list_of_owners>
    ],
    "template": "www.wiota.co",
  }
}
```

## Vertex
### Get all vertices
* **Description:** Get all vertices of a type.
* **Definition:** `GET /<vertex_type>/`
* **Parameters:**
  * `vertex_type`: The vertex type.
* **Example:**
```json
GET /text/
{
  "result": [
    {
      "_cls": "Vertex",
      "_id": "1234567890abcdef",
      "cover": [],
      "deletable": true,
      "host": <host_id>,
      "layout": "",
      "predset": [],
      "public": true,
      "slug": "testing-1",
      "succset": [],
      "text": "this is a test",
      "title": "testing",
      "vertex_type": "text"
    }
  ]
}
```

### Create a new vertex
* **Description:** Get all vertices of a type.
* **Definition:** `POST /<vertex_type>/`
* **Parameters:**
  * `vertex_type`: The vertex type.
* **Example:**
```json
POST /text/
{
  "text": "this is a test",
  "title": "testing",
  "vertex_type": "text"
}
{
  "result": {
    "_cls": "Vertex",
    "_id": "1234567890abcdef",
    "cover": [],
    "deletable": true,
    "host": <host_id>,
    "layout": "",
    "predset": [],
    "public": true,
    "slug": "testing-1",
    "succset": [],
    "text": "this is a test",
    "title": "testing",
    "vertex_type": "text"
  }
}
```

### Get a specific vertex
* **Description:** Get a vertiex by ID
* **Definition:** `GET /<vertex_type>/<id>`
* **Parameters:**
  * `vertex_type`: The vertex type.
  * `id`: The vertex ID.
* **Example:**
```json
GET /text/1234567890abcdef/
{
  "result": {
    "_cls": "Vertex",
    "_id": "1234567890abcdef",
    "cover": [],
    "deletable": true,
    "host": <host_id>,
    "layout": "",
    "predset": [],
    "public": true,
    "slug": "testing-1",
    "succset": [],
    "text": "this is a test",
    "title": "testing",
    "vertex_type": "text"
  }
}
```

### Update a specific vertex
* **Description:** Update a vertiex by ID
* **Definition:** `PUT /<vertex_type>/<id>`
* **Parameters:**
  * `vertex_type`: The vertex type.
  * `id`: The vertex ID.
* **Example:**
```json
PUT /text/1234567890abcdef/
{
  "text": "this is a test UPDATE"
}
{
  "result": "success"
}
```

### Delete a vertex
* **Description:** Delete a vertex by ID. Eventually will remove all edges to this vertex.
* **Definition:** `DELETE /<vertex_type>/<id>`
* **Parameters:**
  * `vertex_type`: The vertex type.
  * `id`: The vertex ID.
* **Note:** This is not currently used by the UI.
* **Example:**
```json
DELETE /text/1234567890abcdef/
{
  "result": "success"
}
```

### Get vertex form
* **Description:** Gets a form for the specified vertex type.
* **Definition:** `GET /<vertex_type>/form/`
* **Parameters:**
  * `vertex_type`: Either a classname which inherits from `Vertex` or a custom vertex type.
* **Example:**
```json
GET /vertex/form/
{
  "result": [
    {
      "label": "Title",
      "name": "title",
      "required": true,
      "type": "text"
    }
  ]
}
```

## Edge
### Create edge
* **Description:** Creates a new edge.
* **Definition:** `POST /edge/`
* **Example:**
```json
POST /edge/
{
  "edges":[
    "555e87a7f431b01f3d85813e","55f466df64636d0009e4d6e0"
  ]
}
{
  "result": "success"
}
```

### Delete edge
* **Description:** Gets a form for the specified vertex type.
* **Definition:** `DELETE /edge/`
* **Example:**
```json
DELETE /edge/
{
  "edges":[
    "555e87a7f431b01f3d85813e","55f466df64636d0009e4d6e0"
  ]
}
{
  "result": "success"
}
```

# Soon-to-be Deprecated Endpoints

## Get Photo
* **Description:** Gets all vertices of type `photo`.
* **Definition:** `GET /photo/`
* **Deprecated:** Use [`GET /<vertex_type>/`](#get-a-specific-vertex) instead.

## Get Audio
* **Description:** Get all vertices of type `audio`.
* **Definition:** `GET /audio/`
* **Deprecated:** Use [`GET /<vertex_type>/`](#get-a-specific-vertex) instead.

## Get User
* **Description:** Supposed to get the the current user. Actually returns the host for some reason.
* **Definition:** `GET /user/`
* **Deprecated:** Use [`GET /host/`](#get-host) instead.

## Put vertex succset
* **Description:** Explicitly sets the succset of a vertex to the payload. Does not update the predset.
* **Definition:** `PUT /<vertex_type>/<id>/succset/`
* **Deprecated:** Use [`POST /edge/`](#create-edge) instead.
