require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "forforf-rgl"
  gem.homepage = "http://github.com/forforf/rgl"
  gem.license = "MIT"
  gem.summary = %Q{"Ruby Graph Library"}
  gem.description = <<-EOF
RGL is a framework for graph data structures and algorithms.

The design of the library is much influenced by the Boost Graph Library (BGL)
which is written in C++ heavily using its template mechanism.

RGL currently contains a core set of algorithm patterns:

* Breadth First Search
* Depth First Search

The algorithm patterns by themselves do not compute any meaningful quantities
over graphs, they are merely building blocks for constructing graph
algorithms. The graph algorithms in RGL currently include:

* Topological Sort
* Connected Components
* Strongly Connected Components
* Transitive Closure
* Transitive Reduction
* Graph Condensation
* Search cycles (contributed by Shawn Garbett)
EOF
  gem.email = "monora@gmail.com"
  gem.authors = ["Horst Duchene"]
  # Include your dependencies below. Runtime dependencies are required when using your gem,
  # and development dependencies are only needed for development (ie running rake tasks, tests, etc)
    gem.add_runtime_dependency 'stream', '>= 0.5'
  #  gem.add_development_dependency 'rspec', '> 1.2.3'
end

Jeweler::RubygemsDotOrgTasks.new

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/Test*.rb'
  test.verbose = true
end

require 'rspec/core'
require 'rspec/core/rake_task'
RSpec::Core::RakeTask.new(:spec) do |spec|
  spec.pattern = FileList['spec/**/*_spec.rb']
end

RSpec::Core::RakeTask.new(:rcov) do |spec|
  spec.pattern = 'spec/**/*_spec.rb'
  spec.rcov = true
end

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "rgl_spec #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
