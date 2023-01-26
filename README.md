# CI CD Jenkins -> AWS

This is a basic application used to showcase **CI-CD** using Jenkins, implemented on an **AWS EC2 Instance**.

## Demo

Below is a demonstration of the **CI-CD** pipeline in action:

- CI
  - Project is updated and the changes are pushed to the `feature-branch`
  - Jenkins catches this and runs `npm test` and if tests pass it merges with `main`.
- CD
  - Once a branch is merged with `main`, a webhook is triggered for Jenkins
  - The application is then built and the changes can be seen live on the site.

---

![GIF](https://github.com/adampaulsackfield/ci-cd-aws/blob/main/images/aws.gif)

## Jenkins - Continuous Integration

Using Jenkins to set up a test environment, which is able to run the `Jest` tests on the application, if all tests pass when we can merge the changes with `main`.

### GitHub Authentication

Using PGP (Pretty Good Privacy), I was able to authorize Jenkins, write permissions to a repository. PGP uses Public/Private Key Pairs to allow secure authentication.
​

### GitHub Webhook

Using _GitHub Webhooks_ I was able to set up a webhook to make a Post request to my Jenkins endpoint, which would start the _Continuous Delivery_ Pipeline to build the application, implementing any changes.
​

## Jenkins - Continuous Delivery

​Using Jenkins to build the application by connecting to the `AWS EC2 Instance`.

### AWS Authentication

​Using PGP (Pretty Good Privacy), I was able to authorize Jenkins, write permissions to an `AWS EC2 Instance`.

### Triggering the Continuous Delivery Pipeline

Using a post-build action, which is triggered on a successful _Continuous Integration_.
