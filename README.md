# Getting Started with Apollo - Python backend

This sample Python backend provides a REST API service that is used with the Getting Started with Apollo UI to show a
simple example of how to connect to and query DataStax Apollo databases.

## Project Layout
- [getting_started_with_apollo.py](getting_started_with_apollo.py) - entrypoint for the backend, registers controller blueprints with Flask app
- [schema.cql](schema.cql) - database schema used by the application
- [service](service/) - acts as the middle-man to take requests from the controllers and calls the corresponding dao methods.
Note how this and [session_manager.py](dao/session_manager.py) are used to share a single DataStax Driver Session across API requests, this is a best practice.
- [model](model/) - defines the Python objects that correspond to the database tables
- [dao](dao/) - methods for accessing the database, contains the DataStax Driver API calls
- [controller](controller/) - defines the API endpoints using Flask decorators

## Setup

If you are familiar with Python, then you've likely gotten your hands on Python virtual environments.
We'll be leveraging pyenv while setting up this backend, which will serve our
Spacecraft frontend that will have you flying through the stars.

If you aren't familiar with Python, hop over to our [official documentation](https://helpdocs.datastax.com/aws/dscloud/apollo/dscloudPythonDriver.html#Installingpyenv,Python,andvirtualenv)
for setting that up on your machine, and come back here after you have it installed ( specifically after Step 5 of the Procedure ).

Now that we have that out of the way, we'll use pyenv to install Python 3.6.9
```
pyenv install 3.6.9
```

Next create a new virtualenv using that Python version we just installed.

```
pyenv virtualenv 3.6.9 apollo-venv
```

Almost off to the races, go ahead and activate that virtualenv

```
pyenv activate apollo-venv
```

Woot, now 3 quick dependencies ( Flask, Flask CORS,  and the DataStax Cassandra Driver )

```
pip install Flask flask-cors cassandra-driver
```

Last one, clone this repo
```
git clone https://github.com/csplinter/getting-started-with-apollo-python.git
```

## Running

If everything above went smoothly, fingers crossed, then we are ready to rock.
Go to the directory that you just cloned this repo into
```
cd getting-started-with-apollo-python
```

Fire up the engines
```
FLASK_ENV=development FLASK_APP=getting_started_with_apollo.py flask run
```

You should be met with the following output, note that it's running on `localhost` and port `5000`
```
 * Serving Flask app "getting_started_with_apollo.py" (lazy loading)
 * Environment: development
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 204-527-831
```
