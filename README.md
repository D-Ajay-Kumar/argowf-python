# ArgoFlow

A Python library for building Argo Workflows in pure object oriented programming style.

## Description

ArgoFlow provides a simple and intuitive Python API for creating Argo Workflows without writing YAML (which I dislike to my core). It allows you to define workflows, tasks, dependencies and artifacts using Python code, making it easier to build dynamic and complex workflows without ever touching YAML.

But if you do still want more granular control, you can use it to generate intermediate Workflow objects as well, for validation or sanity checks, instead of directly submitting the them from the Python script.

## Installation

```bash
pip install argoflow
```

## Quick Start

```python
from argoflow import Workflow, WorkflowTask

# Create a workflow
workflow = Workflow(
    name="my-workflow",
    workflow_server_url="argo-server.example.com",
    namespace="default"
)

# Define tasks
task1 = WorkflowTask(
    name="task-1",
    template="task-1",
    image="python:3.9",
    script="print('Hello from task 1')"
)

task2 = WorkflowTask(
    name="task-2",
    template="task-2",
    image="python:3.9",
    script="print('Hello from task 2')",
    depends_on=[task1]
)

# Add tasks to workflow
workflow.add_tasks(task1, task2)

# Build and save workflow
workflow.save_to_file("workflow.json")

# Submit workflow to Argo
workflow.run_workflow(
    serverUrl="argo-server.example.com",
    executorToken="your-token-here"
)
```

## Features

- Object oriented workflow creation
- Task dependencies and DAG construction
- Input/output artifact management
- Resource allocation (CPU, memory)
- Environment variables and configuration
- Script execution from files or inline code
- Workflow submission to Argo server

## Documentation

For submitting feature requests and contributing to the project, please visit the [GitHub repository](https://github.com/D-Ajay-Kumar/argowf-python).

## License

This project is licensed under the MIT License.