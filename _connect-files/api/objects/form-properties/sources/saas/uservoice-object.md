---
# -------------------------- #
#        CONTENT TYPE        #
# -------------------------- #

content-type: "api-form"
form-type: "source"
key: "source-form-properties-uservoice-object"


# -------------------------- #
#        OBJECT INFO         #
# -------------------------- #

title: "UserVoice Source Form Property"
api-type: "platform.uservoice"
display-name: "UserVoice"

source-type: "saas"
docs-name: "uservoice"

description: ""


# -------------------------- #
#      OBJECT ATTRIBUTES     #
# -------------------------- #

uses-start-date: true

object-attributes:
  - name: "api_key"
    type: "string"
    required: true
    description: |
      The {{ form-property.display-name }} API key. API keys must be generated by a user who can access **Settings** in their {{ form-property.display-name }} account. Refer to [{{ form-property.display-name }}'s documentation](https://developer.uservoice.com/docs/api/v2/getting-started/){:target="new"} for credential generation instructions.
    value: "<API_KEY>"

  - name: "api_secret"
    type: "string"
    required: true
    description: |
      The {{ form-property.display-name }} API secret. API secrets must be generated by a user who can access **Settings** in their {{ form-property.display-name }} account. Refer to [{{ form-property.display-name }}'s documentation](https://developer.uservoice.com/docs/api/v2/getting-started/){:target="new"} for credential generation instructions.
    value: "<SECRET>"

  - name: "subdomain"
    type: "string"
    required: true
    description: "The subdomain of the {{ form-property.display-name }} account to replicate data from. For example: If the full subdomain were `stitch.{{ form-property.display-name | downcase }}.com`, only `stitch` would be provided."
    value: "<SUBDOMAIN>"
---