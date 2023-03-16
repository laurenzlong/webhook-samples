# Webhook Samples

This repo is collection of webhooks data from different platforms that distribute webhooks. This data is used to power https://console.hookdeck.com "Example Webhooks".

## Contributing

### Adding a new provider

1. Add a new directory for the provider in `./providers`

2. Create a `index.json` file in that provider directory. The index.json file needs a `label` which is the publicly reconizable name for the provider, and a set of configs. The `latest_version` represent the most recent version for that provider, if the provider doesn't offer versioning then input `latest`. The `topic_identifier` is optional and represent either a header or body key to extract the topic from the request.

```
{
  "label": "Shopify",
  "configs": {
    "latest_version": "2023-01",
    "topic_identifier": "x-shopify-topic"
  }
}
```

3. [OPTIONAL] Install the dependancies with `yarn install` and start the `requestReceiver.ts` server. You can now send request to http://localhost:9001/:provider/:version and received request will automatically be saved to that provider directory.

Each provider has a set of directory for each version and each version has a file for each topic. The name of the file is the topic and it contains the request data `headers` and `body`.

You can manually enter the data if you'd rather not use the requestReceiver.

## Using the data

The data is packaged into JSON files that are distributed over http. The files can be found on https://samples.hookdeck.com

List of providers: https://samples.hookdeck.com/providers.json
Data for a provider: https://samples.hookdeck.com/providers/shopify/2023-01.json
