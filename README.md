About My Project
=========


## Microservices Voting Application

The Linux stack uses Python, Node.js, .NET Core (or optionally Java), with Redis for messaging and Postgres for storage.

Prerequisites:
```
Docker & Kubernetes installed on system
```
The voting application will be running at [http://localhost:32415](http://localhost:32415), and the results will be at [http://localhost:32414](http://localhost:32414).

## Run the app in Kubernetes
-------------------------

The folder v3 contains the yaml specifications of the Voting App's services.

```
$ kubectl create -f v3/
```

Architecture
-----

![Architecture diagram](architecture.png)

* A front-end web app in python which lets you vote between two options
* A Redis queue which collects new votes
* A .NET core worker which consumes votes and stores them in Postgres
* A Postgres database backed to store votes
* A Node.js webapp which shows the results of the voting in real time


Note
----

The voting application only accepts one vote per client. It does not register votes if a vote has already been submitted from a client.
