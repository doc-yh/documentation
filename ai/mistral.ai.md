# Mistral.AI

Docker compose :&#x20;

```yaml
version: '3.9'

services:
  mistral:
    image: python:3.9
    volumes:
      - .docker/mistral:/app
    working_dir: /app
    environment:
      MISTRAL_API_KEY: F4NyQbhmE5CeAtoXsdYXyMsI9lYiejsE
    command: sh -c "chmod +x /app/start.sh && tail -f /dev/null"
```

{% file src="../.gitbook/assets/mistral.zip" %}
Extraire ce zip dans le dossier docker/mistral
{% endfile %}
