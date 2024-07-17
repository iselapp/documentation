# GitHub Workflows

This directory contains the GitHub Actions workflows for the project.

## Workflows

### Web Scraper (`scraper.yml`)

This workflow automates the process of running the web scrapers and updating the scraped data in the repository.

#### Trigger

The workflow is triggered in two ways:
1. On a schedule (every hour, on the hour)
2. Manually, using the `workflow_dispatch` event

#### Jobs

The workflow consists of a single job named `scrape`, which runs on an Ubuntu runner. The job performs the following steps:

1. Checks out the repository with full history
2. Sets up Python 3.x
3. Installs the required Python dependencies
4. Runs the `run_scrapers.py` script, passing the Supabase URL and key as environment variables (stored as secrets)
5. If there are any changes to the scraped data, commits and pushes the changes to the repository

#### Environment Variables

The workflow uses the following environment variables:
- `SUPABASE_URL`: The URL of the Supabase instance (stored as a secret)
- `SUPABASE_KEY`: The API key for the Supabase instance (stored as a secret)

Make sure to set these secrets in your repository settings before running the workflow.

#### Usage

The workflow will run automatically on the specified schedule. You can also trigger it manually from the GitHub Actions tab in your repository.

## License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.