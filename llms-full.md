# Keboola Full Documentation

> Keboola is a cloud-based data operations platform that empowers businesses to automate data workflows, manage data integration, and enable advanced data analytics. This document provides a comprehensive guide for both new and experienced users, including setup commands, API access details, and key tutorials.

---

## Key Features

- **Data Integration**: Connect, extract, and load data from over 250 sources including databases, SaaS platforms, and APIs.
- **Data Transformation**: Use SQL, Python, R, or other languages to transform and prepare data in a version-controlled environment.
- **Orchestration**: Automate workflows with scheduling tools to keep your data pipelines up-to-date.
- **Data Governance**: Ensure compliance with built-in governance tools like observability, lineage tracking, and auditing.
- **Scalability**: Scale effortlessly with cloud infrastructure to meet growing organizational needs.
- **Collaboration**: Share assets and work collaboratively on data projects to accelerate insights.

---

## Getting Started

### Setting Up Your Keboola Project

1. **Create a Project**:
   - Sign up for a free trial or create a project at [Keboola](https://www.keboola.com).
   - Access the project dashboard after logging in.

2. **Install the CLI**:
   - Install the Keboola CLI for managing projects locally:
     ```bash
     npm install -g @keboola/cli
     ```

3. **Initialize a Local Directory**:
   - Create and initialize a directory for your project:
     ```bash
     mkdir my-kbc-project
     cd my-kbc-project
     kbc init
     ```
   - Provide the API host and token when prompted.

4. **Sync Your Project**:
   - Pull project configurations into your local directory:
     ```bash
     kbc sync pull
     ```

5. **Push Changes Back to Keboola**:
   - After making changes locally, push them to the project:
     ```bash
     kbc sync push
     ```

---

## Tutorials

### Basic Workflow Setup

1. Extract data from a source (e.g., Google Sheets or BigQuery).
2. Transform the data using SQL or Python in Keboola's transformation environment.
3. Load the transformed data into a destination (e.g., Snowflake or Tableau).
4. Automate the pipeline using orchestration tools.

### Advanced Tutorials

- [Connecting BigQuery](https://help.keboola.com/storage/byobq/): Learn how to configure Google Cloud resources for BigQuery integration.
- [Automating Workflows](https://help.keboola.com/tutorial/automate/): Set up orchestrations for end-to-end automation of your pipelines.

---

## API Access Details

Keboola offers several APIs for managing and automating tasks:

| API                     | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| Storage API             | Manage tables, files, and buckets in Keboola Storage.                      |
| Management API          | Oversee projects, users, notifications, and features.                      |
| Queue API               | Run components and manage jobs asynchronously.                             |
| Encryption API          | Handle encryption tasks securely.                                          |
| Transformation API      | Execute SQL/Python/R transformations programmatically.                     |

### Example: Using the Storage API with cURL

To list all buckets in your project:
```bash
curl -X GET https://connection.keboola.com/v2/storage/buckets \
-H "X-StorageApi-Token: YOUR_STORAGE_API_TOKEN"
```

### Storage API Python Client

The Storage API Python Client provides a convenient way to interact with Keboola's Storage API programmatically using Python. Here's how to use it:

#### Installation

```bash
pip3 install keboola.storage.client
```

#### Basic Usage

```python
from keboola.storage.client import Client

# Initialize the client with your Storage API token
client = Client(token='your-storage-api-token')

# List all buckets
buckets = client.buckets.list()

# Create a new bucket
new_bucket = client.buckets.create('new-bucket-name', stage='in', description='My new bucket')

# List tables in a bucket
tables = client.buckets.list_tables('bucket-id')

# Create a new table from CSV file
table = client.tables.create_from_file('bucket-id', 'table-name', 'path/to/file.csv')

# Load data into existing table
client.tables.load(table_id='table-id', file_path='path/to/file.csv', is_incremental=True)

# Export table to CSV
client.tables.export_to_file(table_id='table-id', path_name='path/to/export.csv')
```

#### Advanced Features

1. **Working with Table Metadata**
```python
# Get table metadata
table_info = client.tables.detail('table-id')

# Update table metadata
client.tables.update(
    table_id='table-id',
    new_name='new-table-name',
    new_description='Updated description'
)
```

2. **Managing Table Data**
```python
# Preview table data
preview = client.tables.preview('table-id', limit=100)

# Delete rows from table
client.tables.delete_rows('table-id', where_column='id', where_values=['1', '2', '3'])

# Create table with defined primary key
client.tables.create(
    name='my-table',
    bucket_id='bucket-id',
    primary_key=['id', 'date'],
    column_headers=['id', 'date', 'value']
)
```

3. **Working with Files**
```python
# Upload file to file storage
file_id = client.files.upload_file('path/to/local/file.csv', tags=['tag1', 'tag2'])

# List files with specific tags
files = client.files.list(tags=['tag1'])

# Download file from file storage
client.files.download(file_id, 'path/to/save/file.csv')
```

4. **Error Handling**
```python
from keboola.storage.client import ClientException

try:
    client.buckets.detail('non-existent-bucket')
except ClientException as e:
    print(f"Error occurred: {e}")
```

#### Best Practices

1. **Token Management**
   - Store API tokens securely (e.g., environment variables)
   - Use tokens with minimal required permissions
   - Rotate tokens periodically

2. **Performance Optimization**
   - Use incremental loads when possible
   - Batch operations for multiple files/tables
   - Implement proper error handling

3. **Data Validation**
   - Verify data types before upload
   - Use primary keys when data integrity is crucial
   - Validate CSV formats before loading

4. **Resource Management**
   - Clean up temporary files after processing
   - Monitor storage usage
   - Implement proper logging

### Python Component Library

The Keboola Python Component library provides a robust framework for building Python applications that run in the Keboola Connection environment. It simplifies common tasks related to the Keboola Common Interface, such as configuration handling, I/O operations, logging, and state management.

#### Installation

```bash
pip3 install keboola.component
```

#### Core Modules

1. **Interface Module** (`keboola.component.interface`)
   - Handles core Common Interface tasks
   - Manages environment initialization
   - Processes configuration files
   - Handles data folder operations

2. **DAO Module** (`keboola.component.dao`)
   - Contains data classes for Common Interface objects
   - Manages manifest files and metadata
   - Handles environment variables

3. **Base Module** (`keboola.component.base`)
   - Provides base classes for building Keboola Components
   - Implements common functionality and patterns

#### Basic Component Structure

```python
from keboola.component.base import ComponentBase
from keboola.component import UserException
import logging

class Component(ComponentBase):
    def __init__(self):
        super().__init__()
    
    def run(self):
        # Validate configuration parameters
        self.validate_configuration_parameters(['required_parameter'])
        
        # Access configuration
        params = self.configuration.parameters
        
        # Create output table
        table = self.create_out_table_definition('output.csv', 
                                               incremental=True,
                                               primary_key=['id'])
        
        # Process data and write to output
        with open(table.full_path, 'w') as out_file:
            # Your data processing logic here
            pass
        
        # Write table manifest
        self.write_manifest(table)

if __name__ == "__main__":
    try:
        comp = Component()
        comp.execute_action()
    except UserException as exc:
        logging.exception(exc)
        exit(1)
    except Exception as exc:
        logging.exception(exc)
        exit(2)

#### Advanced Features

1. **Table Schemas**
```python
# Define schema in JSON
{
    "name": "product",
    "primary_keys": ["id"],
    "fields": [
        {
            "name": "id",
            "base_type": "string",
            "nullable": false
        },
        {
            "name": "name",
            "base_type": "string",
            "length": "1000"
        }
    ]
}

# Use schema in component
class Component(ComponentBase):
    def run(self):
        schema = self.get_table_schema_by_name('product')
        table = self.create_out_table_definition_from_schema(schema)
        # Process data using schema-defined structure
```

2. **Sync Actions**
```python
from keboola.component.base import ComponentBase, sync_action
from keboola.component.sync_actions import ValidationResult, MessageType

class Component(ComponentBase):
    @sync_action('testConnection')
    def test_connection(self):
        # Test connection logic
        connection = self.configuration.parameters.get('connection')
        if not self.test_connection(connection):
            raise UserException("Connection failed")
        
    @sync_action('validate')
    def validate_config(self) -> ValidationResult:
        return ValidationResult("Configuration valid", MessageType.SUCCESS)
```

3. **State Management**
```python
class Component(ComponentBase):
    def run(self):
        # Read previous state
        previous_state = self.get_state_file()
        last_run = previous_state.get('last_run')
        
        # Process data incrementally
        new_data = self.process_new_data(since=last_run)
        
        # Save new state
        self.write_state_file({
            "last_run": datetime.now().isoformat(),
            "processed_records": len(new_data)
        })
```

#### Best Practices

1. **Error Handling**
   - Use `UserException` for user-facing errors
   - Implement proper logging
   - Handle configuration validation thoroughly
   - Manage resources properly

2. **Configuration Management**
   - Define required parameters explicitly
   - Validate all inputs
   - Use configuration defaults wisely
   - Document parameter requirements

3. **Data Processing**
   - Implement incremental processing when possible
   - Use table manifests for metadata
   - Handle large datasets efficiently
   - Clean up temporary files

4. **Testing**
   - Write unit tests for components
   - Test sync actions separately
   - Validate configuration scenarios
   - Test error handling

#### Common Use Cases

1. **Data Extraction**
```python
class Extractor(ComponentBase):
    def run(self):
        # Create output table
        table = self.create_out_table_definition('extracted_data.csv')
        
        # Extract data
        data = self.extract_from_source()
        
        # Write to CSV
        with open(table.full_path, 'w') as out_file:
            writer = csv.DictWriter(out_file, fieldnames=data[0].keys())
            writer.writeheader()
            writer.writerows(data)
        
        # Write manifest
        self.write_manifest(table)
```

2. **Data Transformation**
```python
class Transformer(ComponentBase):
    def run(self):
        # Read input table
        input_table = self.get_input_tables()[0]
        
        # Create output table
        output_table = self.create_out_table_definition('transformed.csv')
        
        # Transform data
        with open(input_table.full_path, 'r') as in_file:
            reader = csv.DictReader(in_file)
            transformed_data = [self.transform_row(row) for row in reader]
        
        # Write transformed data
        with open(output_table.full_path, 'w') as out_file:
            writer = csv.DictWriter(out_file, fieldnames=transformed_data[0].keys())
            writer.writeheader()
            writer.writerows(transformed_data)
```

---

## Command Line Interface (CLI)

The CLI allows advanced users to manage projects efficiently:

### Common Commands

| Command                  | Description                                                              |
|--------------------------|--------------------------------------------------------------------------|
| `kbc init`              | Initialize a new local directory for your project.                      |
| `kbc sync pull`         | Pull project configurations into the local directory.                   |
| `kbc sync push`         | Push local changes back to the project.                                 |
| `kbc diff`              | Show differences between local and remote configurations.               |
| `kbc create config`     | Create a new configuration interactively or via command options.         |

### Example Workflow with CLI

1. Create a new extractor configuration:
   ```bash
   kbc create config -b main -c ex-generic-v2 -n wikipedia
   ```
2. Edit the configuration file (`config.json`) to specify the source (e.g., Wikipedia).
3. Push the configuration to Keboola:
   ```bash
   kbc sync push
   ```

---

## Key Setup Tutorials

### Connecting BigQuery

1. Create a Google Cloud folder and project.
2. Set up a service account with appropriate roles (e.g., BigQuery Data Viewer).
3. Add credentials to Keboola as an extractor configuration.
4. Test the connection by running an extraction job.

### Automating Workflows with Orchestrator

1. Define tasks in the Orchestrator UI.
2. Schedule tasks based on dependencies or time intervals.
3. Monitor job execution logs for troubleshooting.

---

## Advanced Features

- **Reverse ETL**: Push transformed data back into operational systems like Salesforce or HubSpot.
- **Data Catalog**: Discover and govern datasets across projects.
- **AI Assistant**: Accelerate workflows with AI-driven suggestions for transformations.

---

## Support Resources

- [User Documentation](https://help.keboola.com/): Step-by-step guides for all features.
- [Developer Documentation](https://developers.keboola.com/): API references and CLI commands.
- [Community Forums](https://community.keboola.com/): Engage with other users for tips and best practices.
- [Support Team](mailto:support@keboola.com): Contact us for personalized assistance.

---

Experience the full power of Keboola by combining automation, scalability, and collaboration into your data workflows!


Citations:
[1] https://help.keboola.com/tutorial/onboarding/
[2] https://help.keboola.com/tutorial/
[3] https://help.keboola.com
[4] https://help.keboola.com/storage/byobq/
[5] https://developers.keboola.com/cli/getting-started/
[6] https://developers.keboola.com/overview/api/
[7] https://help.keboola.com/overview/
[8] https://developers.keboola.com/cli/commands/