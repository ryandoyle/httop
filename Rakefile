require 'erb'

# useful variables
pwd = File.dirname(__FILE__)

task :rpm do
  version = '1.0'
  release = "#{number_of_git_commits}+#{git_branch}+git#{git_head_sha}"
  puts "Building rpm #{version}-#{release}"
  f = File.new('httop.spec', File::CREAT|File::TRUNC|File::RDWR, 0644)
  f.write ERB.new(File.read('httop.spec.erb')).result(binding)
  f.close
  `rpmbuild -ba -v httop.spec --define "_topdir #{pwd}/rpm" --define "_sourcedir #{pwd}"`
end

task :clean do
  `rm -rf rpm`
end

def number_of_git_commits
    `git log | grep commit | wc -l`.strip
end 

def git_branch
    `git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/\* //'`.strip
end

def git_head_sha
    `git rev-parse --short HEAD`.strip
end
