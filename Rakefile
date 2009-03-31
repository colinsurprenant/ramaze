begin; require 'rubygems'; rescue LoadError; end

require 'rake'
require 'rake/clean'
require 'rake/gempackagetask'
require 'time'
require 'date'

PROJECT_SPECS = Dir['spec/{examples,ramaze,snippets}/**/*.rb']
PROJECT_MODULE = 'Ramaze'
PROJECT_JQUERY_FILE = 'lib/proto/public/js/jquery.js'
PROJECT_README = 'README.markdown'
PROJECT_RUBYFORGE_GROUP_ID = 3034
PROJECT_COPYRIGHT = [
  "#          Copyright (c) #{Time.now.year} Michael Fellinger m.fellinger@gmail.com",
  "# All files in this distribution are subject to the terms of the Ruby license."
]

# To release the monthly version do:
# $ PROJECT_VERSION=2009.03 rake release

GEMSPEC = Gem::Specification.new{|s|
  s.name         = 'ramaze'
  s.author       = "Michael 'manveru' Fellinger"
  s.summary      = "Ramaze is a simple and modular web framework"
  s.description  = s.summary
  s.email        = 'm.fellinger@gmail.com'
  s.homepage     = 'http://github.com/manveru/org'
  s.platform     = Gem::Platform::RUBY
  s.version      = (ENV['PROJECT_VERSION'] || Date.today.strftime("%Y.%m.%d"))
  s.files        = `git ls-files`.split("\n").sort
  s.has_rdoc     = true
  s.require_path = 'lib'
  s.bindir = "bin"
  s.executables = ["ramaze"]
  s.rubyforge_project = "ramaze"
  s.add_dependency('rack', '>= 0.9.9') # lies!
  s.add_dependency('manveru-innate', '>= 2009.04')
  s.post_install_message = <<MESSAGE.strip
============================================================

Thank you for installing Ramaze!
You can now do create a new project:
# ramaze --create yourproject

============================================================
MESSAGE
}

Dir['tasks/*.rake'].each{|f| import(f) }

task :default => [:bacon]

CLEAN.include %w[
  **/.*.sw?
  *.gem
  .config
  **/*~
  **/{data.db,cache.yaml}
  *.yaml
  pkg
  rdoc
  ydoc
  *coverage*
]
