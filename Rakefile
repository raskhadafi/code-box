#!/usr/bin/env rake
require "bundler/gem_tasks"

require 'rubygems'
require 'rake'
require 'bundler'
Bundler::GemHelper.install_tasks


require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end


begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/test_*.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end


require 'rdoc/task'
require "code-box/version"
Rake::RDocTask.new do |rdoc|
  version = CodeBox::VERSION

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "code-box #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end

task :default => :test
