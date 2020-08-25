# website_hugo

I was getting an error when deployoing on Netflify. Found ths solution:

Create "netlify.toml" with the following contents:

[build]
  publish = "public"
  command = "hugo"

[context.production.environment]
  HUGO_VERSION = "0.74.3"
  HUGO_ENV = "production"
  HUGO_ENABLEGITINFO = "true"
  
[context.branch-deploy.environment]
  HUGO_VERSION = "0.74.3"

[context.deploy-preview.environment]
  HUGO_VERSION = "0.74.3"
  
[context.deploy-preview]
  command = "hugo -b $DEPLOY_PRIME_URL --buildFuture"

[context.branch-deploy]
  command = "hugo -b $DEPLOY_PRIME_URL --buildFuture"