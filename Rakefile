require 'rake'

desc "Default task: test"
task :default => [ :test ]

# Run the unit tests
require 'rake/testtask'
Rake::TestTask.new { |t|
  t.libs << "test"
  t.test_files = Dir['test/*_test.rb'] + Dir['test/test_*.rb']
  t.verbose = true
}

# Generate the RDoc documentation
require 'rdoc/task'
RDoc::Task.new { |rdoc|
  rdoc.rdoc_dir = 'doc'
  rdoc.rdoc_files.add('lib')
  rdoc.main     = "PDF::Toolkit"
  rdoc.title    = rdoc.main
  rdoc.options << '--inline-source'
}

# Create compressed packages
require 'rake/packagetask'
require 'rake/gempackagetask'
spec = eval(File.read("pdf-toolkit.gemspec"))
Rake::GemPackageTask.new(spec) do |p|
  p.gem_spec = spec
  p.need_tar = true
  p.need_zip = true
end

