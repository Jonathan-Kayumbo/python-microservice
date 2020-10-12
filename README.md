# python-microservice


This is a basic approach of building a Microservice on top of Flask, with some useful packages like:

- [Flask](http://flask.pocoo.org/)
- [Flask-Injector](https://pypi.python.org/pypi/Flask-Injector)
- [Connexion](https://github.com/zalando/connexion)

# Requirements

 builds a microservice to index rooms information coming from another service (crawler). This service will be responsible for indexing the information into Elasticsearch.

The indexing will be a process of:

- Validate and sanitize the data
- Get some metadata from the room information like geolocalization
- Upload the given images URL to [Amazon S3](https://github.com/boto/boto), not set though
- Send an event to [RabbitMQ](https://github.com/pika/pika) every time a new room has been indexed serializing the payload with Avro.


**Endpoints**:

|Method|URI|Description| Status |
|------|---|-----------|--------|
| POST | /room | it will receive the room payload, and it will proceed to index it | **Development** |
| PATCH | /room/{id} | this PATCH method will allow us to make changes on the indexed item | Not started |
| DELETE | /room/{id} | this method will remove the room from the index | Not started |
| GET | /room/{id} | this method will return the room data for a given room id | Not started |
| GET | /health-check | This endpoint retuns the state of the service | Not started |

# Running the environment

You need to have Docker installed , after that, run this command `docker-compose build && docker-compose up -d`.
