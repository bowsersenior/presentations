!SLIDE code commandline incremental

# 1 : Bundler

    $ bundle gem my_gem           
          create  my_gem/Gemfile                
          create  my_gem/Rakefile               
          create  my_gem/.gitignore
          create  my_gem/my_gem.gemspec
          create  my_gem/lib/my_gem.rb
          create  my_gem/lib/my_gem/version.rb



!SLIDE code small

# Gemfile

    @@@ ruby
    source "http://rubygems.org"

    # Specify your gem's dependencies in my_gem.gemspec
    gemspec   
    
    #-# Look ma, no gems!
    #-# NOTE: '#-#' comments are not Bundler-generated


!SLIDE code evensmaller

# my_gem.gemspec

    @@@ ruby
    # -*- encoding: utf-8 -*-
    $:.push File.expand_path("../lib", __FILE__)  #-# put 'lib' in your path
    require "my_gem/version"                      #-# makes versioning easy

    Gem::Specification.new do |s|
      s.name        = "my_gem"
      s.version     = MyGem::VERSION              #-# loaded from my_gem/version
      s.authors     = ["Fakey McFakerson"]
      s.email       = ["fakey@example.com"]
      s.homepage    = ""
      s.summary     = %q{TODO: Write a gem summary}
      s.description = %q{TODO: Write a gem description}

      s.rubyforge_project = "my_gem"              #-# who uses rubyforge these days?

      s.files         = `git ls-files`.split("\n")  #-# how clever!
      s.test_files    = `git ls-files -- {test,spec,features}/*`.split("\n")
      s.executables   = `git ls-files -- bin/*`.split("\n").map{ |f| File.basename(f) }
      s.require_paths = ["lib"]
    end
    
    #-# Many more options. 
    #-# For more info see: http://docs.rubygems.org/read/chapter/20
    
!SLIDE code evensmaller

# httparty.gemspec

    @@@ ruby
    # -*- encoding: utf-8 -*-
    $:.push File.expand_path("../lib", __FILE__)
    require "httparty/version"

    Gem::Specification.new do |s|
      s.name        = "httparty"
      s.version     = HTTParty::VERSION
      s.platform    = Gem::Platform::RUBY
      s.authors     = ["John Nunemaker", "Sandro Turriate"]
      s.email       = ["nunemaker@gmail.com"]
      s.homepage    = "http://httparty.rubyforge.org/"
      s.summary     = %q{Makes http fun! Also, makes consuming restful web services dead easy.}
      s.description = %q{Makes http fun! Also, makes consuming restful web services dead easy.}

      s.add_dependency 'crack', HTTParty::CRACK_DEPENDENCY    #-# needed for `gem install`

      s.add_development_dependency "activesupport", "~> 2.3"  #-# needed to hack on this gem
      s.add_development_dependency "cucumber",      "~> 0.7"
      s.add_development_dependency "fakeweb",       "~> 1.2"
      s.add_development_dependency "rspec",         "~> 1.3"
      s.add_development_dependency "mongrel",       "1.2.0.pre2"

      s.post_install_message = "When you HTTParty, you must party hard!" #-# Nice touch!

      s.files         = `git ls-files`.split("\n")
      s.test_files    = `git ls-files -- {test,spec,features}/*`.split("\n")
      s.executables   = `git ls-files -- bin/*`.split("\n").map{ |f| File.basename(f) }
      s.require_paths = ["lib"]
    end
    
    
!SLIDE code small

# lib/my_gem.rb

    @@@ ruby
    require "my_gem/version"  
    #-# Chop up your code into smaller files like:
    #-#   'lib/my_gem/some_feature.rb'
    #-#   'lib/my_gem/some_other_feature.rb'    
    #-#
    #-# Then require the files here:
    #-#   require 'my_gem/some_feature'
    #-#   require 'my_gem/some_other_feature'

    module MyGem
      # Your code goes here...
    end
    
    #-# Try to keep this file small, 
    #-# unless you can fit all your code in one file.  
    
    
!SLIDE code small
    
# lib/my_gem/version.rb
    
    @@@ ruby
    module MyGem
      VERSION = "0.0.1"
    end
    
    
    
!SLIDE code small 

# Rakefile

    @@@ ruby
    require 'bundler/gem_tasks'

    #-# We'll revisit this file later
    
    

!SLIDE code small

# .gitignore

    @@@ sh
    
    *.gem         #-# from `gem build my_gem.gemspec`
    .bundle       
    Gemfile.lock  #-# see: http://sn.im/gemfiledotlock
    pkg/*
    
    
!SLIDE smbullets incremental

# Resources on `bundler gem`

* [http://railscasts.com/episodes/245-new-gem-with-bundler](http://railscasts.com/episodes/245-new-gem-with-bundler)
* [http://gembundler.com/rubygems.html](http://gembundler.com/rubygems.html)
* ![TheMoreYouKnow](the_more_you_know.jpg)