require 'rake'

namespace :site do
  desc "Generate the site"
  task :build do
    sh "bundle exec jekyll build"
  end

  desc "Generate the site, test it and push changes to remote server"
  task :travis => 'site:build' do
    # Detect pull request
    if ENV['TRAVIS_PULL_REQUEST'] != "false"
      puts 'Pull request detected. Not proceeding with deploy.'
      puts ENV['TRAVIS_PULL_REQUEST'].to_s
      exit
    end

    # Push to remote server via rsync
    puts sh 'echo "$PWD"'
    sh 'rsync -avz --delete _site/ deploy@www.eveofdarkness.org:/home/deploy/www'
    # Commit and push to github
    puts "Pushed latest master to the server"
  end
end
