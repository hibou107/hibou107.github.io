Title: Designing a json migration tool
Date: 2017-12-22 10:20
Category: scala
Tags: scala, json

# The problems

Json is probably the most popular data format today. It's used both for data exchange (between front-end and backend for example). It's also used to store inside database like `MongoDB`, even [`postgresql`](https://www.postgresql.org/docs/9.3/static/functions-json.html) supports json data type.

Working with `json` means defining 2 functions:

* A Writer that converts an object into `json` format
* A Reader that reads a `json` and produces an object

An example of this use case is:

```scala
case class Model(x: String, y: String)
```

In [`play-json`](https://github.com/playframework/play-json), we can define a `Format` and uses the macro helper to automatically define a `Reader` and a `Writer` of `Model`

```scala
implicit val modelFormat: Format[Model] = Json.format[Model]
```

This is an example value:

```json
{ “x”: “toto”, “y”: “tata” }
```
