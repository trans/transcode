require "rubygems"
require "tmpdir"
require "bundler/setup"
require "jekyll"

# Change your GitHub reponame eg. "kippt/jekyll-incorporated"
GITHUB_REPONAME = "trans/trans.github.com"
GH_PAGES = false

desc "bundle install and clone site and wiki"
task :setup do
  system "bundle install"
  get_wiki
  get_site
end

desc "update wiki"
task :update do
  $stderr.puts "[UPDATE]"

  if File.exist?("_site/.git")
    Dir.chdir("_site") do
      system "git pull origin master"
    end
  else
    get_site
  end

  if File.exist?('_wiki/.git')
    Dir.chdir("_wiki") do
      system "git pull origin master"
    end
  else
    get_wiki
  end
end

desc "generate blog files"
task :build => [:update] do
  $stderr.puts "[BUILD]"
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => "_source",
    "destination" => "_site"
  })).process
end

desc "build and deploy site"
task :deploy => [:build] do
  $stderr.puts "[DEPLOY]"
  Dir.chdir "_site" do
    message = "Site updated at #{Time.now.utc}"
    #unless File.exist?(".git")
    #  system "git init"
    #  system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
    #end
    #system "git pull origin master"
    system "git add ."
    system "git commit -m #{message.inspect}"
    if GH_PAGES
      system "git push origin master:refs/heads/gh-pages --force"
    else
      system "git push origin master"
    end
  end
end

desc "build and deploy site via copy"
task :publish => [:build] do
  Dir.mktmpdir do |tmp|
    cp_r "_site/.", tmp
    Dir.chdir tmp do
      message = "Site updated at #{Time.now.utc}"
      #unless File.exist?(".git")
      #  system "git init"
      #  system "git remote add origin git@github.com:#{GITHUB_REPONAME}.git"
      #end
      #system "git pull origin master"
      system "git add ."
      system "git commit -m #{message.inspect}"
      if GH_PAGES
        system "git push origin master:refs/heads/gh-pages --force"
      else
        system "git push origin master"
      end
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

#
def get_wiki
  unless File.directory?('_wiki')
    system "git clone git@github.com:#{GITHUB_REPONAME}.wiki.git _wiki"
  end
end

#
def get_site
  unless File.directory?('_site')
    system "git clone git@github.com:#{GITHUB_REPONAME}.git _site"
  end
end
