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