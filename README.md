# CXS Examples - Python
This project contains runnable examples for interacting with CXS. The examples are written in python.

## Setup and Requirements
This project uses [Poetry](https://python-poetry.org/) for deterministic builds and dependency management.

1. [Python 3.8 or greater](https://www.python.org/downloads/) is expected
1. Install Poetry using the appropriate instructions for your operating system: https://python-poetry.org/docs/
1. Make sure that your tools are up to date (poetry requires current virtualenv)
   ```
   python -m pip install --upgrade pip
   pip install -U virtualenv
   ```
1. From the project root install dependencies using Poetry (Poetry will create and manage a python virtual environment for you)
   ```
   poetry install
   ```
## The Environment File
1. Create a file named `.env` in the project root
2. The contents should look like this
```
PADLOCK_URL=https://padlock.stress.concentrixcxs.com
TEXT_URL=https://text.stress.concentrixcxs.com
EMPEROR_PENGUIN_URL=https://penguin.stress.concentrixcxs.com
HOMING_PIGEON_URL=wss://homing-pigeon.stress.concentrixcxs.com

CXS_USERNAME=your_username
CXS_PASSWORD=your_password

TENANT_ID=your-tenant-uuid

CATEGORY_MODEL_ID=your-category-model-uuid
SENTIMENT_LEXICON_MODEL_ID=your-sentiment-lexicon-model-uuid
```

## Running Examples
To run an example script you simply identify the name of the file you wish to run in the `/examples` directory (not including the "`.py`") then from the project root run
```
poetry run example <example_file_name>
```

---

### Sync Categorization
**WARNING:** This method is scheduled for deprecation. This technique bypasses the CXS job queuing system.
```
poetry run example sync_categorization
```
This example shows you how to retrieve categorization results from the "Text" API, directly.

----

### Async Categorization
```
poetry run example async_categorization
```
This example shows you how to create an asynchronous job for retrieving categorization results. This will be the preferred technique going forward as it allows our system to better schedule large volumes of data from multiple tenants, concurrently.
