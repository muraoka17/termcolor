# -*- coding: utf-8 -*-
$:.unshift File.dirname(__FILE__) + '/lib/'
require 'termcolor'
require 'rspec/core'
require 'rspec/core/rake_task'

task :default => :spec

RSpec::Core::RakeTask.new(:spec) do |spec|
  spec.pattern = FileList['spec/**/*_spec.rb']
end

desc 'Generate gemspec'
task :gemspec do |t|
  open('termcolor.gemspec', "wb" ) do |file|
    file << <<-EOS
# -*- coding: utf-8 -*-
Gem::Specification.new do |s|
  s.name = 'termcolor'
  s.version = '#{TermColor::VERSION}'
  s.summary = %q(Termcolor is a library for ANSI color formatting like HTML for output in terminal.)
  s.description = %q(Termcolor is a library for ANSI color formatting like HTML for output in terminal. '<red>red</red>'.termcolor #=> "\e[31mred\e[0m")
  s.files = %w( #{Dir['lib/**/*.rb'].join(' ')}
                #{Dir['spec/**/*.rb'].join(' ')}
                #{Dir['examples/**/*.rb'].join(' ')}
                README.rdoc
                History.txt
                Rakefile )
  s.add_dependency("highline", ">= 1.5.0")
  s.author = 'jugyo'
  s.email = 'jugyo.org@gmail.com'
  s.homepage = 'http://github.com/jugyo/termcolor'
  s.rubyforge_project = 'termcolor'
  s.has_rdoc = true
  s.rdoc_options = ["--main", "README.rdoc", "--exclude", "spec"]
  s.extra_rdoc_files = ["README.rdoc", "History.txt"]
end
    EOS
  end
  puts "Generate gemspec"
end

desc 'Generate gem'
task :gem => :gemspec do |t|
  system 'gem', 'build', 'termcolor.gemspec'
end
