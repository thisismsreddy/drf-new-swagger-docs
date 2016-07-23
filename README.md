# drf-new-swagger-docs
Djangorestframework 3.4 and new swagger documentation supports login and etc.... 

To up and running with new restframework3.4 and swagger2 all we have to do is.. add this to urls file, You can find this is urls.py

```
from rest_framework import renderers, response, schemas
from rest_framework.decorators import api_view, renderer_classes
from rest_framework_swagger.renderers import OpenAPIRenderer, SwaggerUIRenderer


@api_view()
@renderer_classes([SwaggerUIRenderer, OpenAPIRenderer, renderers.CoreJSONRenderer])
def schema_view(request):
    generator = schemas.SchemaGenerator(title='Your Docs name API')
    return response.Response(generator.get_schema(request=request))


And add this to urls

url('^$', schema_view),
```

- Note: you have to add this to your existing urls.py
