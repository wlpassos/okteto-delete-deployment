# This is action is to delete resources in Okteto Cloud

# GitHub Actions for Okteto Cloud

## Automate your development workflows using Github Actions and Okteto Cloud
GitHub Actions gives you the flexibility to build an automated software development workflows. With GitHub Actions for Okteto Cloud you can create workflows to build, deploy and update your applications in [Okteto Cloud](https://cloud.okteto.com).

Get started today with a [free Okteto Cloud account](https://cloud.okteto.com)!

## Github Action for Deleting Resources in Okteto Cloud

You can use this action to delete resources in your Okteto Cloud namespace. This is equivalent to running `kubectl delete -f $manifest`.

## Inputs

### `namespace`

The Okteto namespace to use. If not specified it will use the namespace specified by the `namespace` action.

### `manifest`

Path to the Kubernetes manifest. Can be a file or a directory. It defaults to `k8s.yml`.

## Example usage

This example runs the login action, activates a namespace and deletes a deployment.

```yaml
# File: .github/workflows/workflow.yml
on: [push]

name: example

jobs:

  devflow:
    runs-on: ubuntu-latest
    steps:
    
    - uses: okteto/login@master
      with:
        token: ${{ secrets.OKTETO_TOKEN }}
    
    - name: "Activate personal namespace"
      uses: okteto/namespace@master
      with:
        name: cindylopez

    - name: "Delete Deployment"
      uses: wlpassos/okteto-delete-resource@master
      with:
        manifest: deployment.yaml
```

