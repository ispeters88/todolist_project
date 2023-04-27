require 'rake/testtask'
require 'find'
require 'bundler/gem tasks'

desc 'Say hello'
task :hello do
  puts "Hello there. This is the 'hello' task"
end

desc 'List files'
task :list do
  Find.find(Dir.pwd) do |path|
    if FileTest.directory?(path) && File.basename(path).start_with?('.')
        Find.prune
    elsif File.basename(path).start_with?('.') || File.directory?(path)
      next
    else
      puts path
    end
  end
end

desc 'Run tests'
task :default => :test

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end
