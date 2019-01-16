---
title: Source and Destination Data Types
permalink: /replication/supported-data-types
keywords: supported datatypes data types datatype
tags: [replication]
layout: general
sidebar: stitchnav

content-type: "select-data"
toc: true
weight: 4

summary: "TO-DO"

sections: 
  - content: |
      When data is extracted from a source, Stitch also extracts metadata about the fields selected for replication. Stitch uses this metadata to determine a field's data type and then store its values as the correct data type during loading.

      In this guide, we'll cover:

      1. [How data typing works](#how-data-typing-works),
      2. [The data type Stitch supports](#supported-source-data-types), and
      3. 


  - title: "How data typing works"
    anchor: "how-data-typing-works"
    content: |
      {% assign stitch-data-types = site.data.stitch.supported-data-types.stitch-types %}

      During a replication job, Stitch examines metadata about the fields selected for replication. Stitch uses this metadata to determine the data type's accurate equivalent for your destination.

      In general, Stitch will use the following data types to store data in your destination:

      <table class="attribute-list">
      {% for stitch-type in stitch-data-types %}
      <tr>
      <td class="attribute-name">
      {{ stitch-type.name | upcase }}
      </td>
      <td class="attribute-description">
      All <a href="#{{ stitch-type.category | append:"-data-types" }}">{{ stitch-type.category | replace:"-"," " }} source data types</a>
      </td>
      </tr>
      {% endfor %}
      </table>


      Refer to the [TODO]() section for info on how specific supported source types are mapped to the destination types listed here.

      **Note:** Stitch may convert some data types to a type supported by your destination. For example: If a destination only supports an `INTEGER` data type, `BIGINT` data may be stored as `INTEGER`. Refer to the documentation for your destination for more info.

    # subsections:
    #   - title: "Step 1: Examine source data type"
    #     anchor: "step-1--source-data-type"
    #     content: |
    #       The first step in data typing is examining the source column's data type, which occurs during the Extraction phase of a replication job. When Stitch extracts data from a source, it will examine a column's metadata to determine its data type.

    #       If it's a [supported data type](), Stitch will extract the data for the column and continue with the replication process.


    #   - title: "Step 2: Map Stitch data type to destination data type"
    #     anchor: "step-3--map-to-destination"
    #     content: |
    #       Every destination handles data typing differently. To account for this, in Stitch the final data type of a column in the destination is dependent on the type of destination being used. 

    #        For example: Some destinations may have [TBD].

    #        By performing this process, Stitch can ensure that the most accurate data type is being used to store your data in the destination of your choosing.

# To ensure data is typed and accurately loaded, Stitch only replicates data from the data types listed in this section. The columns in the table below are as follows:

# - **Source data type**: The name of the supported data type
# - **Stitch data type**: The general type Stitch 'maps' the source type to. **This is not necessarily the data 

# Note that:

# - Unless otherwise noted, a data type is supported for any integration
# - If a data type isn't listed, Stitch doesn't currently support replication for that data type. [Replicating columns with unsupported data types can lead to issues with replication](#sync-unsupported-data-types).

  - title: "Supported source data types"
    anchor: "supported-source-data-types"
    content: |
      {% assign all-supported-source-types =  %}

      {% assign all-type-categories = "boolean|date-and-time|numeric|string" | split:"|" %}

      {% for type-category in all-type-categories %}
      ### {{ type-category | capitalize | replace:"-"," " | append:" data types" }} {#{{ type-category | append:"-data-types" }}}

      Stitch supports replicating data for the following {{ type-category | replace:"-"," " }} data types:

      {% assign these-stitch-data-types = stitch-data-types | where:"category",type-category | sort:"name" %}

      {% for stitch-type in these-stitch-data-types %}
      {% assign supported-data-types = site.data.stitch.supported-data-types.supported-source-types | where:"stitch-type",stitch-type.name | sort:"name" %}

      {% for supported-type in supported-data-types %}
      - `{{ supported-type.name | upcase }}`
      {% endfor %}
      {% endfor %}
      {% endfor %}




# {% assign supported-data-types = all-supported-data-types | where:"stitch-type",stitch-type.name | sort:"name" %}

# <table class="attribute-list">
# <tr>
# <td class="attribute-name">
# <strong>Source data type</strong>
# </td>
# <td class="attribute-description">
# <strong>Destination data type</strong>
# </td>
# </tr>
# {% for source-type in all-supported-source-types %}
# <tr>
# <td class="attribute-name">
# {{ source-type.name | upcase }}
# </td>
# <td class="attribute-description">
# {{ source-type.stitch-type | upcase }}
# </td>
# </tr>
# {% endfor %}
# </table>

# {% include replication/templates/data-types/data-type-formatting.html formatting="tabs" integration_name="postgres" display_name="PostgreSQL" %}

    subsections:
      - title: "Unsupported data types"
        anchor: "sync-unsupported-data-types"
        content: |
          If a column you want to sync has a Status of `Not Supported`, the root cause may be an [unsupported data type or insufficient user permissions]({{ link.troubleshooting.unsupported-data-types | prepend: site.baseurl }}).

          Columns containing data types that aren't supported may prevent an entire table from replicating. 

          If you determine a non-replicating column contains an unsupported data type, you'll need to de-select it to allow the table to successfully replicate.

  - title: "Source data types to Stitch data types"
    anchor: "source-to-stitch"
    content: |

  - title: "Stitch data types to destination"
    anchor: "stitch-to-destination"
    content: |


---
{% include misc/data-files.html %}





---

## Columns with mixed data types {#mixed-data-types}

Occasionally Stitch will encounter a column that contains more than one data type. As Stitch requires that there be only one data type per column to properly type and store your data, columns containing multiple data types may be "split" to ensure all values are correctly typed.

For example: an `order_confirmed` column is synced and typed as `BOOLEAN`. In a subsequent sync, Stitch detects `VARCHAR` values in this column.

As a result, Stitch will create an additional column to accommodate the `VARCHAR` values. The new column name will be the original name appended with the data type: `order_confirmed__string`

How columns are named depends on the type of destination being used to warehouse data. Refer to the [Mixed Data Types guide for more info]({{ link.destinations.storage.column-splitting | prepend: site.baseurl }}).

---