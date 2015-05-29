# beanie

My capistrano defaults. Change the following files, then merge the files into a rails project.

## Gemfile
```
group :development do
  # Use Capistrano for deployment
  gem 'capistrano'
  # rails specific capistrano funcitons
  gem 'capistrano-rails'
  # integrate bundler with capistrano
  gem 'capistrano-bundler'
  # if you are using RBENV
  gem 'capistrano-rbenv'
  # if you want to use sudo with capistrano
  gem 'sshkit-sudo'
end

gem 'figaro' # for environment variables
gem 'unicorn'
```

### deploy.rb
```
set :application, 'APP_NAME'
set :deploy_user, 'DEPLOY_USER'
set :repo_url, "git@github.com:GITHUB_USER/#{fetch(:application)}.git"
```

### production.rb
```
set :server_name, "WEBSITE_DOMAIN"
server 'SERVER_IP', user: 'deployer', roles: %w{app db web}
```
