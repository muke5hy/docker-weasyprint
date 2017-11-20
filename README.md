# docker-weasyprint

[![Build Status](https://travis-ci.org/muke5hy/docker-weasyprint.svg?branch=master)](https://travis-ci.org/muke5hy/docker-weasyprint)

[Weasyprint](http://weasyprint.org/) as a microservice in a docker image.

# Usage

Run the docker image, exposing port 5001

```
docker run -p 5001:5001 muke5hy/weasyprint
```

A `POST` to port `/pdf` on port 5001 with an html body with give a response containing a PDF. The filename may be set using a query parameter, e.g.:

```
curl -X POST -d @source.html http://127.0.0.1:5001/pdf?filename=result.pdf
```

This will use the file `source.html` and return a response with `Content-Type: application/pdf` and `Content-Disposition: inline; filename=result.pdf` headers.  The body of the response will be the PDF.

In addition `/health` is a health check endpoint and a `GET` returns 'ok'.
