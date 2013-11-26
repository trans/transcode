require "rubygems"
require "tmpdir"

require "bundler/setup"
require "jekyll"

# Change your GitHub reponame eg. "kippt/jekyll-incorporated"
GITHUB_REPONAME = "trans/trans.github.com"

namespace :site do
  desc "Clone wiki site"
  task :setup do
    sh "git clone git@github.com:trans/trans.github.com.wiki.git _wiki"
  end

  desc "Generate blog files"
  task :generate do
    Jekyll::Site.new(Jekyll.configuration({
      "source"      => "_source",
      "destination" => "_site"
    })).process
  end

  #desc "Generate and publish blog to gh-pages"
  #task :publish => [:generate] do
  #  Dir.mktmpdir do |tmp|
  #    cp_r "_site/.", tmp
  #    Dir.chdir tmp
  #    system "git init"
  #    system "git add ."
  #    message = "Site updated at #{Time.now.utc}"
  #    system "git commit -m #{message.inspect}"
  #    system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
  #    system "git push origin master:refs/heads/gh-pages --force"
  #  end
  #end
end
