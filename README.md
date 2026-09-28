# CI/CD Tools and Practices Final Project Template

## ci-cd-final-project

CI/CD final project for Continuous Integration and Continuous Delivery (CI/CD).
GitHub Actions validates the Flask counter service on pushes and pull requests.
OpenShift Pipelines cleans a dedicated workspace, clones the source, checks code
quality, runs the tests, builds the image, and deploys the service.

This educational project retains the course's Python 3.9 and dependency pins for
lab compatibility. These legacy dependencies are not a production baseline.

This repository contains the template to be used for the Final Project for the Coursera course **CI/CD Tools and Practices**.

## Usage

This repository is to be used as a template to create your own repository in your own GitHub account. No need to Fork it as it has been set up as a Template. This will avoid confusion when making Pull Requests in the future.

From the GitHub **Code** page, press the green **Use this template** button to create your own repository from this template.

Name your repo: `ci-cd-final-project`.

## Setup

After entering the lab environment you will need to run the `setup.sh` script in the `./bin` folder to install the prerequisite software.

```bash
bash bin/setup.sh
```

Then you must exit the shell and start a new one for the Python virtual environment to be activated.

```bash
exit
```

## Tasks

- `.github/workflows/workflow.yml`: flake8 linting and nose tests with coverage.
- `.tekton/tasks.yml`: workspace cleanup and nose test tasks.
- `setup.cfg`: nose coverage targets the actual `service` package.

Local checks in the course environment:

```bash
flake8 service --count --select=E9,F63,F7,F82 --show-source --statistics
flake8 service --count --max-complexity=10 --max-line-length=127 --statistics
nosetests -v --with-spec --spec-color --with-coverage --cover-package=service
```

Install the project tasks in the assigned lab namespace:

```bash
kubectl apply -f .tekton/tasks.yml
```


## License

Licensed under the Apache License. See [LICENSE](/LICENSE)

## Author

Skills Network

## <h3 align="center"> © IBM Corporation 2023. All rights reserved. <h3/>
