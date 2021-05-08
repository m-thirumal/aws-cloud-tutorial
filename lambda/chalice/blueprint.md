# Blueprint
#### Chalice blueprints are used to organize your application into logical components

1. Create `chalicelib` folder with the logical components

        mkdir chalicelib
        touch chalicelib/__init__.py
        touch chalicelib/blueprints.py

2. Configure the `decoration` in `chalicelib/blueprints.py` file:


        from chalice import Blueprint


        extra_routes = Blueprint(__name__)


        @extra_routes.route('/foo')
        def foo():
            return {'foo': 'bar'}
    

    The `__name__` is used to denote the import path of the blueprint. This name must match the import name of the module so the function can be properly imported when running in Lambda. We’ll now import this module in our app.py and register this blueprint. We’ll also add a route in our app.py directly:


    3. Import in `app.py`

        ```
        from chalice import Chalice
        from chalicelib.blueprints import extra_routes

        app = Chalice(app_name='blueprint-demo')
        app.register_blueprint(extra_routes)


        @app.route('/')
        def index():
            return {'hello': 'world'}
        ```
        
