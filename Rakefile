require "rubygems"
require "tmpdir"
require "bundler/setup"
require "jekyll"

# Change your GitHub reponame eg. "kippt/jekyll-incorporated"
GITHUB_REPONAME = "trans/trans.github.com"

desc "Bundle install and clone wiki."
task :setup do
  sh "bundle install"
  sh "git clone git@github.com:#{GITHUB_REPONAME}.wiki.git _wiki"
end

desc "Update wiki."
task :update do
  Dir.chdir("_wiki") do
    sh "git pull origin master"
  end
end

desc "Generate blog files"
task :generate do
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => "_source",
    "destination" => "_site"
  })).process
end

desc "Generate and publish site"
task :publish => [:generate] do
  Dir.mktmpdir do |tmp|
    cp_r "_site/.", tmp
    Dir.chdir tmp do
      unless File.exist?(".git")
        system "git init"
        system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
      end
      system "git add ."
      message = "Site updated at #{Time.now.utc}"
      system "git commit -m #{message.inspect}"
      #system "git push origin master:refs/heads/gh-pages --force"
      system "git push origin master"
    end
  end
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

