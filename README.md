# biomaj-watcher

Web interface for biomaj (https://github.com/osallou/biomaj) 

# License

AGPL

# Requirements

biomaj3

# Install

    python setup.py install

# Development - build web app

Install npm

    git checkout -b develop

in biomajwatcher/webapp:

    npm install -g grunt
    npm install -g bower
    grunt install
    bower install
    grunt

# Configuration

Configuration is done in development.ini or production.ini

    global_properties = PATH_TO_BIOMAJ_global.properties
    
    # List of user ids with admin priviledges.
    # Users need to be create or be ldap users if ldap
    # is configured in global.properties
    admin = admin, jdoe
    
    # Celery configuration over mongodb, mongodb url
    BROKER_URL = mongodb://localhost/biomaj_celery


# Running

## Development

    pserve development.ini

## Production

    gunicorn -p /var/run/gunicorn_bmaj.pid --log-config=production.ini --paste production.ini &


Web server will start to listen on port 6543 by default. Update ini files to
customize web configuration.


# Background processing (Optional)

To allow banks update/removal by authenticated user, Celery is needed. Celery can run on same node, or multiple distant ones to execute bank updates.

    pceleryd development.ini/production.ini

One can use flower to monitor celery.

# User creation

python db/seed.py --config production.ini --user yyy --pwd xxxx


# Credits

Signin image from http://bootsnipp.com/snippets/featured/google-style-login