Drupal Tools
================

<!-- WARNING: THIS FILE WAS AUTOGENERATED! DO NOT EDIT! -->

## Install

``` sh
pip install drupal_tools
```

## How to use

[See the documentation](./api.html) for full details of the Omeka API
Client.

Please create `.env` file in the root of your project with the following
content:

    DRUPAL_URL=http://example.org/drupal
    DRUPAL_USERNAME=username
    DRUPAL_PASSWORD=password

``` python
from drupal_tools.api import DrupalAPIClient

df = pd.read_csv("./uuids.csv")

uuids = []

for i, row in df.iterrows():
    uuid = row["asset_uuid"]

    uuids.append(uuid)

DRUPAL_URL, DRUPAL_USERNAME, DRUPAL_PASSWORD = DrupalAPIClient.load_credentials("../.env")

drupal = DrupalAPIClient(DRUPAL_URL, DRUPAL_USERNAME, DRUPAL_PASSWORD)

nids = drupal.get_nids(uuids, "a-label", "field_item_id", "IN")

results = drupal.delete_from_nids(nids)
```
