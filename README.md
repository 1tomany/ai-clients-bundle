# PHP AI Bundle for Symfony

This package wraps the `1tomany/php-ai` library into an easy to use Symfony bundle.

## Installation

Install the bundle using Composer:

```
composer require 1tomany/php-ai-bundle
```

## Configuration

Create a file named `php_ai.yaml` in `config/packages/` and add the following lines:

```yaml
php_ai:
    gemini:
        api_key: '%env(GEMINI_API_KEY)%'
        # http_client: 'http_client'
        # serializer: 'serializer'
    openai:
        api_key: '%env(OPENAI_API_KEY)%'
        # http_client: 'http_client'
        # serializer: 'serializer'

when@dev:
    php_ai:
        mock:
            enabled: true
```

By default, the `http_client` and `serializer` properties in the `gemini` and `openai` blocks use the `@http_client` and `@serializer` services defined in a standard Symfony application. You're free to use your own scoped HTTP Client or Serializer services.

If you wish to disable a vendor, simply delete the configuration block from the file. For example, if your application only uses Gemini, you would delete the `openai` block:

```yaml
php_ai:
    gemini:
        api_key: '%env(GEMINI_API_KEY)%'
```

You'll also have to define the API keys in your `.env` file or by using the [Symfony Secrets](https://symfony.com/doc/current/configuration/secrets.html) component.

## Credits

- [Vic Cherubini](https://github.com/viccherubini), [1:N Labs, LLC](https://1tomany.com)

## License

The MIT License
