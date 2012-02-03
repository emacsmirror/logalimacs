# -*- mode: ruby; coding: utf-8 -*-

# This program is Rakefile for marmalade(Repository site for Emacs lisp). 
# You can possible to create package-directory for marmalade.

# Input your configuration
PACKAGE_NAME = "logalimacs"
PACKAGE_VERSION = "0.0.2"
REQUIREMENTS = ["logalimacs.el", "logalimacs-rurema.el"]
DESCRIPTION = "Front-end of logaling-command for Ruby gem"

# Depending on other package
# @example specify as bellow:
#   [["package1", "version1"], ["package2", "virsion2"], ...]
DEPENDENCIES = [["popwin", "0.4"], ["popup", "0.4"]]

#--rakefile--
task :default => :package

desc "Package #{PACKAGE_NAME}"
task :package => :bundle do
  sh("tar", "cvf", "#{MARMALADE_PACKAGE_NAME}.tar", MARMALADE_PACKAGE_NAME)
end

desc "Bundle #{PACKAGE_NAME}"
task :bundle => :init do
  rm_rf(MARMALADE_PACKAGE_NAME)
  rm_rf("#{MARMALADE_PACKAGE_NAME}.tar")
  mkdir(MARMALADE_PACKAGE_NAME)
  REQUIREMENTS.each do |file|
    cp(file, MARMALADE_PACKAGE_NAME)
  end
  open("#{MARMALADE_PACKAGE_NAME}/#{PKG_EL}", "w") do |content|
    content.print(PKG_EL_CONTENT)
  end
end

desc "Sets constant"
task :init => "Rakefile" do
  dependencies = "'("
  DEPENDENCIES.each {|pkg, version| dependencies << %Q{(#{pkg} "#{version}")}}
  dependencies << ")"
  MARMALADE_PACKAGE_NAME = "#{PACKAGE_NAME}-#{PACKAGE_VERSION}"
  PKG_EL = "#{PACKAGE_NAME}-pkg.el"
  PKG_EL_CONTENT = <<-ELISP
(define-package "#{PACKAGE_NAME}" "#{PACKAGE_VERSION}" "#{DESCRIPTION}" #{dependencies})
ELISP
end