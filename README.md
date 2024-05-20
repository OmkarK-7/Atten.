# Atten
Example Question 
Give me the top 5 customers with the most number of orders.

Desired Output (Example):
```javascript
 #RequiredColumns
 {
  "table_information": [
    {
      "table_name": "customer_0",
      "table_description": "Stores detailed customer information and behavior",
      "primary_key_column": [
        "customer_id"
      ],
      "columns": [
        {
            "name": "customer_id",
            "description": "Unique identifier for the customer",
            "data_type": "STRING",
            "format": "",
            "is_pii_column": "Y",
            "enum": [],
            "dimension_group": "",
            "is_nullable": "N"
        },
        {
            "name": "first_name",
            "description": "Customer's first name",
            "data_type": "STRING",
            "format": "CamelCase",
            "is_pii_column": "Y",
            "enum": [],
            "dimension_group": "customer_dimension_group",
            "is_nullable": "N"
        },
        {
            "name": "last_name",
            "description": "Customer's last name",
            "data_type": "STRING",
            "format": "CamelCase",
            "is_pii_column": "Y",
            "enum": [],
            "dimension_group": "customer_dimension_group",
            "is_nullable": "N"
        }
      ]
    },
    {
      "table_name": "order",
      "table_description": "Stores detailed records of customer orders",
      "primary_key_column": [
        "order_id",
        "order_item_id"
      ],
      "columns": [
                {
            "name": "order_id",
            "description": "Unique identifier for the order",
            "data_type": "STRING",
            "format": "",
            "is_pii_column": "N",
            "enum": [],
            "is_nullable": "N"
        },
        {
            "name": "customer_id",
            "description": "Unique identifier for the customer",
            "data_type": "STRING",
            "format": "",
            "is_pii_column": "Y",
            "enum": [],
            "is_nullable": "N"
        }
      ]
    }
  ]
 }
  
 #TableRelationship
 {
  "relationships": [
    {
      "FromTable": "customer_0",
      "FromColumn": [
        "customer_id"
      ],
      "ToTable": "order",
      "ToColumn": [
        "customer_id"
      ]
    }
  ]
 }
```
This can be more simplified as; We have two sections: Required Columns and Table Relationships.

**Table: `customer_0`**
- Description: Stores detailed customer information and behavior.
- Primary Key Column: customer_id
- Columns:

| Column Name | Description | Data Type | Format | PII Column | Nullable |
|-------------|-------------|-----------|--------|------------|----------|
| `customer_id` | Unique identifier for the customer | STRING | N/A | Yes | No |
| `first_name` | Customer's first name | STRING | CamelCase | Yes | No |
| `last_name` | Customer's last name | STRING | CamelCase | Yes | No |

**Table: `order`**
- Description: Stores detailed records of customer orders.
- Primary Key Columns: order_id, order_item_id
- Columns:

| Column Name | Description | Data Type | Format | PII Column | Nullable |
|-------------|-------------|-----------|--------|------------|----------|
| `order_id` | Unique identifier for the order | STRING | N/A | No | No |
| `customer_id` | Unique identifier for the customer | STRING | N/A | Yes | No |


# LLM_finetuning

**What does finetuning do for the model**
- Let's you put more data into the model than what fits into the prompt.
- Get's the model to learn the data, rather than just get access to it.

  The example can be simple:
  - __General doctor Vs Specialist__
  - Here you can fine-tune the doctor with the required study of specialization of maybe to Dermatologist.
  - So, rather than a general doctor, a dermatologist will be able to provide appropriate info on your desired set of problems.

**Benefits of fine-tuning your own LLM**
- Performance:
  - Stop Hallucinations
  - Increase consistency
  - Reduce unwanted info
- Privacy:
  - Prevent leakages.
- Reliability:
  - Lower Latency
  - control uptime (Time for which the system will be functional).

# Pre-Training {Base Model} (Expensive and time-consuming) 
- Pretraining consists of the extreme beginning of the training of the model. This model is just a next word predictor which is not even good enough.
  - Model has zero knowledge
  - Can't even form English words.
- Next token prediction
- Has giant corpus of text data (Often scraped from the internet "unlabeled"
