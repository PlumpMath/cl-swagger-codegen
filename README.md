# cl-swagger-codegen #
lisp code-generator for swagger

A swagger codegen is to build APIs quicker and improve consumption of your Swagger-defined APIs in every popular language with Swagger Codegen. (http://swagger.io/swagger-codegen/)

cl-swagger-codegen generates API client for common lisp. 

## Test ##

You can build a client, (for example `test1.lisp`) against the swagger sample petstore API as follows:
`(generate-client "http://petstore.swagger.io/v2/swagger.json" "test1.lisp")`

You can add a new pet to the store as follows:

```
(setf body (cl-json:encode-json-to-string '((id . 0)
                                            (:category . ((:id . 0) (:name . "string")))
                                            (:name . "doggie")
                                            ("photoUrls" . #("string"))
                                            (:tags . (((:id . 0)
                                                       (:name . "string"))))
                                            (:status . "available"))))

(convert-json #'post-pet-call "pet" body)

```

For json object, cl-swagger-codegen uses `cl-json`. 

```
(cl-json:encode-json-to-string '((id . 0)
                                (:category . ((:id . 0) (:name . "string")))
                                (:name . "doggie")
                                ("photoUrls" . #("string"))
                                (:tags . (((:id . 0)
                                (:name . "string"))))
                                (:status . "available")))
```

for json object :

```
{
  "id": 0,
  "category": {
    "id": 0,
    "name": "string"
  },
  "name": "doggie",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}
```
