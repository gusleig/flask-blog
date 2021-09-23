# Flask Microblog Example

Credits to [Miguel Grinberg](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world)

## Setup Env
```
set ELASTICSEARCH_URL=http://localhost:9200

set FLASK_ENV=development
```

If you set FLASK_ENV=production in your terminal session and then trigger the duplicate username bug one more time, you are going to see a slightly more friendly error page.

## Download and Install ElasticSearch

Tutorial [here](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xvi-full-text-search)

Installing Elasticsearch
There are several ways to install Elasticsearch, including one-click installers, zip file with the binaries that you need to install yourself, and even a Docker image. 

The documentation has an Installation page with detailed information on all these options. If you are using Linux, you will likely have a package available for your distribution. 

If you are using a Mac and have Homebrew installed, then you can simply run brew install elasticsearch.

Once you install Elasticsearch on your computer, you can verify that it is running by typing http://localhost:9200 in your browser's address bar, which should return some basic information about the service in JSON format.



Download (Server): [here](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)

on Windows:

```
cd c:\elasticsearch-7.14.2

.\bin\elasticsearch.bat
```

Since I will be managing Elasticsearch from Python, I will also be using the Python client library:

```
(venv) $ pip install elasticsearch
```

Testing
```
>>> es = Elasticsearch('http://localhost:9200')
 
>>> es.index(index='my_index', id=1, body={'text': 'this is a test'})
>>> es.index(index='my_index', id=2, body={'text': 'a second test'})

>>> es.search(index='my_index', body={'query': {'match': {'text': 'this test'}}})

>>> es.indices.delete('my_index')
```

## SMTP debugging

```
(venv) $ python -m smtpd -n -c DebuggingServer localhost:8025


export MAIL_SERVER=smtp.googlemail.com
export MAIL_PORT=587
export MAIL_USE_TLS=1
export MAIL_USERNAME=<your-gmail-username>
export MAIL_PASSWORD=<your-gmail-password>


```

If you are planning to test sending of emails you have the same options I mentioned in Chapter 7. If you want to use an emulated email server, Python provides one that is very handy that you can start in a second terminal with the following command:
```
(venv) $ python -m smtpd -n -c DebuggingServer localhost:8025
```
To configure for this server you will need to set two environment variables:

```
(venv) $ export MAIL_SERVER=localhost
(venv) $ export MAIL_PORT=8025
```