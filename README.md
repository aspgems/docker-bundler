# docker-bundler
Docker container to run bundle install when you need to install gems from private repos

## Motivation
At the moment docker does not support ssh forwarding in building time, so when you need to bundle install gems from private repos, you should be doing bundle install as a separate step from the rest of the building process.

## Instructions
You can use this container by running the following command fron the root of your application

```bash
docker run --rm -it -v $(pwd):/app -v ~/.ssh/id_rsa:/root/.ssh/id_rsa aspgems/bundler
```
This command will install gems in vendor/bundle directory

**Configuring your public key:** This assumes that your id_rsa file resides in
~/.ssh/id_rsa. If you have your public key in other location, you should change that route.

**File permissions:** The files generated under vendor/bundle will belong to root user. You may need the ownership of this directory to match your user.

```bash
sudo chown -R your_user:your_group vendor/bundle
```
