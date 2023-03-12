# Contribute to Marzban
Thanks for considering contributing to Marzban!

## Questions

Please don't ask your questions in issues. Instead, use one of the following ways to ask:
- Ask on our telegram group: [@Gozargah_Marzban](https://t.me/gozargah_marzban)
- Ask on our [GitHub Discussions](https://github.com/gozargah/marzban/discussions) for long term discussion or larger questions.


## Reporting issues

Include the following information in your post:
- Describe what you expected to happen.
- Describe what actually happened. Include server logs or any error that browser shows.
- If possible, post your xray json config file and what you have set in env (by censoring critical information).
- Also tell the version of Marzban, Xray and docker (if you use docker) you are using.


# Submitting a Pull Request
If there is not an open issue for what you want to submit, prefer opening one for discussion before working on a PR. You can work on any issue that doesn't have an open PR linked to it or a maintainer assigned to it. These show up in the sidebar. No need to ask if you can work on an issue that interests you.

## Branches
When starting development on this project, please make sure to create a new branch off the `dev` branch. This helps to keep the `master` branch stable and free of any development work that may not be complete or fully tested.

## Project Structure
```
.
├── app                      # Backend code (FastAPI - Python)
│   └── dashboard            # Frontend code (React - Typescript)
└── xray_api                 # Client of Xray's gRPC API
```

## Backend
Backend is built using FastAPI and uses SQLAlchemy as the ORM for database operations. All Pydantic models can be found in the `app/models` directory, while all database-related operations and models are in the `app/db` directory. The migration scripts for the database (Alembic) can be found in the `app/db/migrations` directory.

### Python Code Formatting
To maintain consistency in the codebase, we require all code to be formatted using 
```bash
autopep8 <file> --max-line-length 120
```

## Frontend
Frontend is pre-built and served by FastAPI from the `app/dashboard/build` directory. To rebuild the frontend, first make sure you have the necessary dependencies installed by running `npm install` in the `app/dashboard` directory. Then, simply remove the `app/dashboard/build` directory and run the Python code again, and it will rebuild the frontend automatically.

### Components Library
Frontend uses `Chakra-UI` as the component library, so please adhere to the Chakra-UI approach when contributing. Strive to create components that are cohesive and serve a single purpose. Keep in mind that readability and maintainability are more important than brevity, so prioritize those factors when writing your code.

## Debug Mode
To run the project in debug mode with auto-reload, you can set the environment variable `DEBUG` to `true`. then by running the `main.py`, the backend and frontend will run separately on different ports.

Note that you must first install the necessary npm packages by running npm install inside the app/dashboard directory before running in debug mode.
```bash
cd app/dashboard
npm install
cd ../..
```

If you run the project with debug mode off and delete the `app/dashboard/build` directory, the frontend will be rebuilt automatically on the next run. However, no rebuild will occur while inside debug mode."
