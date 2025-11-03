# Data Processing Workflows

This directory contains workflows focused on data transformation, enrichment, and processing tasks.

## Available Workflows

### CSV Data Transformer
**File:** `csv-data-transformer.json`

**Description:** A basic workflow that demonstrates how to transform CSV data, add metadata, and convert it to JSON format.

**Features:**
- Processes incoming data
- Adds processing timestamp
- Adds status field
- Converts to JSON format

**Use Cases:**
- Data migration tasks
- ETL operations
- Data format conversion
- Batch data processing

**Setup:**
1. Import the workflow into N8N
2. Configure the input source for your CSV data
3. Customize the transformation logic in the Function node
4. Set up the output destination

**Nodes Used:**
- Start node
- Function node (for transformation)
- Convert to File node

**Customization:**
Modify the `Transform Data` function node to implement your specific data transformation logic.
