require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "mongo_mapper"
    gem.summary = %Q{Awesome gem for modeling your domain and storing it in mongo}
    gem.email = "nunemaker@gmail.com"
    gem.homepage = "http://github.com/jnunemaker/mongomapper"
    gem.authors = ["John Nunemaker"]
    gem.rubyforge_project = "mongomapper"
    
    gem.add_dependency('activesupport', '>= 2.3')
    gem.add_dependency('mongo', '0.15.1')
    gem.add_dependency('luisbebop-validatable', '1.7.4')
    
    gem.add_development_dependency('jnunemaker-matchy', '0.4.0')
    gem.add_development_dependency('shoulda', '2.10.2')
    gem.add_development_dependency('timecop', '0.3.1')
    gem.add_development_dependency('mocha', '0.9.4')
  end
  
  Jeweler::RubyforgeTasks.new do |rubyforge|
    rubyforge.doc_task = "rdoc"
  end
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: sudo gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

namespace :test do
  Rake::TestTask.new(:units) do |test|
    test.libs << 'lib' << 'test'
    test.pattern = 'test/unit/**/test_*.rb'
    test.verbose = true
  end
  
  Rake::TestTask.new(:functionals) do |test|
    test.libs << 'lib' << 'test'
    test.pattern = 'test/functional/**/test_*.rb'
    test.verbose = true
  end
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

begin
  require 'cucumber/rake/task'
  Cucumber::Rake::Task.new(:features)
rescue LoadError
  task :features do
    abort "Cucumber is not available. In order to run features, you must: sudo gem install cucumber"
  end
end

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  if File.exist?('VERSION.yml')
    config = YAML.load(File.read('VERSION.yml'))
    version = "#{config[:major]}.#{config[:minor]}.#{config[:patch]}"
  else
    version = ""
  end

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "MongoMapper #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
