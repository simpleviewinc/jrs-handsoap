# -*- coding: utf-8 -*-
begin
  require 'jeweler'
  #require 'rubygems'
  #gem :jeweler
  Jeweler::Tasks.new do |gemspec|
    gemspec.name = "handsoap"
    gemspec.summary = "Handsoap is a library for creating SOAP clients in Ruby"
    gemspec.email = ["troelskn@gmail.com","frontend@unwire.dk"]
    gemspec.homepage = "http://github.com/unwire/handsoap"
    gemspec.description = gemspec.summary
    gemspec.authors = ["Troels Knak-Nielsen", "Jimmi Westerberg"]
    gemspec.requirements << "You need to install either \"curb\" or \"httpclient\", using one of:\n    gem install curb\n    gem install httpclient"
    gemspec.requirements << "It is recommended that you install either \"nokogiri\" or \"libxml-ruby\""
    gemspec.files = FileList['lib/**/*.rb', 'generators/handsoap/templates', 'generators/**/*', '[A-Z]*.*'].to_a
  end
  Jeweler::GemcutterTasks.new
rescue LoadError => err
  puts "Jeweler not available. Install it with: sudo gem install jeweler"
  p err
end

desc "Generates API documentation"
task :rdoc do
  sh "rm -rf doc && rdoc lib"
end

require 'rake/testtask'
namespace :test do
  desc "Remove temporary files generated by test case"
  task :cleanup do
    puts "Clearing temporary files"
    sh "rm -rf tests/rails_root"
  end
  Rake::TestTask.new :test do |test|
    # Rake::Task['test:cleanup'].invoke
    test.test_files = FileList.new('tests/**/*_test.rb') do |list|
      list.exclude 'tests/benchmark_integration_test.rb'
      list.exclude 'tests/service_integration_test.rb'
      list.exclude 'tests/httpauth_integration_test.rb'
    end
    test.libs << 'tests'
    test.verbose = true
  end
end

desc "Run tests and clean up afterwards"
task :test => ["test:cleanup", "test:test", "test:cleanup"]

task :default => [:test]

