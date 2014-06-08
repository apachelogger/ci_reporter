#--
# Copyright (c) 2006-2014 Nick Sieger <nicksieger@gmail.com>
# See the file LICENSE.txt included with the distribution for
# software license details.
#++

require 'bundler/setup'

begin
  require 'hoe'
  Hoe.plugin :git
  require File.dirname(__FILE__) + '/lib/ci/reporter/version'
  hoe = Hoe.spec("ci_reporter") do |p|
    p.version = CI::Reporter::VERSION
    p.group_name = "caldersphere"
    p.readme_file = "README.rdoc"
    p.urls = ["https://github.com/nicksieger/ci_reporter"]
    p.author = "Nick Sieger"
    p.email = "nick@nicksieger.com"
    p.readme_file = 'README.rdoc'
    p.summary = "CI::Reporter allows you to generate reams of XML for use with continuous integration systems."
    p.changes = p.paragraphs_of('History.txt', 0..1).join("\n\n")
    p.description = p.paragraphs_of('README.rdoc', 0...1).join("\n\n")
    p.extra_rdoc_files += ["README.rdoc"]
    p.test_globs = ["spec/**/*_spec.rb"]
    p.extra_deps     << [ 'builder',   '>= 2.1.2'  ]
    p.extra_dev_deps << [ 'hoe-git',   '~> 1.5.0'  ]
    p.clean_globs += ["spec/reports", "acceptance/reports"]
    p.license 'MIT'
  end
  hoe.spec.rdoc_options += ["-SHN", "-f", "darkfish"]

  task :gemspec do
    File.open("#{hoe.name}.gemspec", "w") {|f| f << hoe.spec.to_ruby }
  end
rescue LoadError
  puts "You really need Hoe installed to be able to package this gem"
end
