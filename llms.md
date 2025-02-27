# Keboola

> Keboola is a cloud-based data operations platform that empowers businesses to automate data workflows, manage data integration, and enable advanced data analytics. Our mission is to simplify data processes and democratize access to powerful data tools, allowing organizations to focus on extracting insights and driving value from their data.

## Key Features

- **Data Integration**: Connect, extract, and load data from various sources effortlessly. Our extensive library of over 250 ready-to-use connectors covers databases, SaaS platforms, and APIs.
- **Data Transformation**: Transform and prepare your data using SQL, Python, R, and other languages within our collaborative and version-controlled environment.
- **Orchestration**: Automate workflows with our robust scheduling and orchestration tools, ensuring your data is always up-to-date and readily available.
- **Data Governance**: Maintain data quality and compliance with our built-in governance features, providing observability, lineage tracking, and auditing capabilities.
- **Scalability**: Leverage the power of the cloud to scale your data operations, accommodating the growing needs of your organization with ease.
- **Collaboration**: Work seamlessly with your team, sharing data assets and collaborating on data projects to accelerate insights and decision-making.

## Additional Features

- **AI Assistant**: Leverage our AI-powered assistant to streamline data operations and gain insights.
- **Reverse ETL**: Enable data activation by pushing transformed data back to operational systems.
- **Data Catalog**: Facilitate data discovery and governance with our comprehensive data catalog.
- **Multi-level Access Control**: Establish granular access controls for different users within your organization.
- **End-to-End Encryption**: Ensure data security with robust encryption measures, including SSL encryption for API connections.

## Use Cases

Keboola has proven effective across various industries and use cases:

- **Financial Reporting**: Automate financial reporting processes, enabling faster and more accurate insights.
- **Customer Analytics**: Integrate and analyze customer data from multiple sources to drive personalized marketing and improve customer experience.
- **Operational Efficiency**: Streamline data workflows to enhance operational efficiency and reduce manual data processing tasks.
- **Data-Driven Decision Making**: Empower decision-makers with real-time, accurate data through automated dashboards and reports.

## Success Stories

- **Pincho Nation**: Achieved insights at double speed and six-figure revenue growth by leveraging Keboola for data integration and analysis.
- **Apify**: Saved 3.5 engineering days per month while doubling upsells through improved data management and analytics.
- **P3 Logistic Parks**: Optimized data management across 11 countries, leading to improved operational efficiency and decision-making.

## Getting Started

1. [Sign up for a free trial](https://www.keboola.com) to explore Keboola's capabilities.

## Documentation

- [User Documentation](https://help.keboola.com/): Comprehensive guides and tutorials for end-users to maximize the platform's capabilities.
- [Developer Documentation](https://developers.keboola.com/): Resources for developers integrating or extending Keboola's functionalities.

## APIs and Integration

Keboola offers a suite of APIs to facilitate seamless integration and automation:

- [Storage API](https://developers.keboola.com/overview/api/storage/): Manage data storage, including tables and files.
- [Management API](https://developers.keboola.com/overview/api/management/): Oversee projects, users, and notifications.
- [Encryption API](https://developers.keboola.com/overview/api/encryption/): Handle data encryption tasks.
- [Queue API](https://developers.keboola.com/overview/api/queue/): Execute components and manage jobs.
- [OAuth Broker API](https://developers.keboola.com/overview/api/oauth-broker/): Manage OAuth authorizations for components.
- [Orchestrator API](https://developers.keboola.com/overview/api/orchestrator/): Automate and schedule tasks within your project.

## Storage API Python Client

The Storage API Python Client (`kbcstorage`) provides client methods to interact with Keboola Connection Storage API. This API client enables you to get data from KBC and store data in KBC, with comprehensive support for working with buckets, tables, and workspaces.

### Installation

```bash
pip3 install kbcstorage
```

Or install directly from GitHub:

```bash
pip3 install git+https://github.com/keboola/sapi-python-client.git
```

### Client Class Usage

```python
from kbcstorage.client import Client

client = Client('https://connection.keboola.com', 'your-token')

# Get table data into local file
client.tables.export_to_file(table_id='in.c-demo.some-table', path_name='/data/')

# Save data
client.tables.create(name='some-table-2', bucket_id='in.c-demo', file_path='/data/some-table')

# List buckets
client.buckets.list()

# List bucket tables
client.buckets.list_tables('in.c-demo')

# Get table info
client.tables.detail('in.c-demo.some-table')
```

### Endpoint Classes Usage

You can also use the endpoint classes directly:

```python
from kbcstorage.tables import Tables
from kbcstorage.buckets import Buckets

# Initialize Tables endpoint
tables = Tables('https://connection.keboola.com', 'your-token')

# Get table data into local file
tables.export_to_file(table_id='in.c-demo.some-table', path_name='/data/')

# Save data
tables.create(name='some-table-2', bucket_id='in.c-demo', file_path='/data/some-table')

# Initialize Buckets endpoint
buckets = Buckets('https://connection.keboola.com', 'your-token')

# List buckets
buckets.list()

# List bucket tables
buckets.list_tables('in.c-demo')

# Get table info
tables.detail('in.c-demo.some-table')
```

### Best Practices

- Store API tokens securely using environment variables
- Implement proper error handling
- Use appropriate endpoint classes for specific operations
- Clean up temporary files after processing

## Python Component Library

Our Python Component library enables developers to build custom Python applications that run in the Keboola environment:

```bash
pip3 install keboola.component
```

### Key Features

- **Common Interface Integration**: Seamless handling of Keboola's Common Interface
- **Configuration Management**: Easy access to component configuration
- **I/O Operations**: Simplified table and file operations
- **Error Handling**: Built-in exception handling and logging
- **State Management**: Support for stateful operations
- **Sync Actions**: Implementation of configuration validation and testing

### Example Component

```python
from keboola.component.base import ComponentBase
from keboola.component import UserException

class MyComponent(ComponentBase):
    def __init__(self):
        super().__init__()
    
    def run(self):
        # Get configuration
        params = self.configuration.parameters
        
        # Create output table
        table = self.create_out_table_definition('results.csv')
        
        # Process data
        with open(table.full_path, 'w') as out_file:
            # Your data processing logic here
            pass
        
        # Write manifest
        self.write_manifest(table)

if __name__ == "__main__":
    try:
        comp = MyComponent()
        comp.execute_action()
    except (UserException, Exception) as exc:
        logging.exception(exc)
        exit(1)

### Best Practices

- Use proper error handling with `UserException`
- Validate configuration parameters
- Implement incremental processing when possible
- Write comprehensive tests
- Clean up temporary files
- Document configuration requirements

For detailed examples and API reference, visit our [Developer Documentation](https://developers.keboola.com/).

## Tutorials and Examples

- [Getting Started with Keboola](https://help.keboola.com/tutorials/): Step-by-step tutorials to help new users onboard and utilize the platform effectively.
- [Advanced Data Transformations](https://help.keboola.com/tutorials/advanced-transformations/): In-depth guides on performing complex data transformations using Keboola.

## Community and Support

- Join our [Community Forums](https://community.keboola.com/) to engage with other users and seek assistance.
- Stay updated with the latest news and best practices on our [Blog](https://blog.keboola.com/).
- Contact our support team for personalized assistance and guidance.

Experience the power of Keboola and transform your data operations today!