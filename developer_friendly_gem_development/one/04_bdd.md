!SLIDE bullets incremental

# 3 : Cucumber + rspec setup
* Cukes for a gem?!?
* Yes!



!SLIDE code

# gem_tasks/cucumber.rake

    @@@ ruby
    
    require 'cucumber/rake/task'

    Cucumber::Rake::Task.new(:features) do |t|
      t.fork = false
    end
    
    
        
!SLIDE code evensmaller

# features/load.feature

    @@@ ruby

    Feature: --configure option

      Use the --configure option on the command line to generate configuration
      files.

      The only supported argument, so far, is "autotest", which creates a .rspec
      file in your project root directory. When autotest sees this file, it knows
      to load RSpec's Autotest subclass.

      Scenario: .rspec file already exists
        Given a file named ".rspec" with:
          """
          --color
          """
        When I run `rspec --configure autotest`
        Then the output should contain ".rspec file already exists, so nothing was changed."    
    
    
!SLIDE bullets

# Awesome cukes to learn from
* [https://github.com/myronmarston/vcr](https://github.com/myronmarston/vcr)
* [https://github.com/cucumber/cucumber-rails](https://github.com/cucumber/cucumber-rails)
* [https://github.com/rspec/rspec-core](https://github.com/rspec/rspec-core)
* [http://relishapp.com/myronmarston/vcr](http://relishapp.com/myronmarston/vcr)
* [http://cukes.info](http://cukes.info)


!SLIDE code

# gem_tasks/rspec.rake

    @@@ ruby

    require 'rspec/core/rake_task'

    desc "Run RSpec"
    RSpec::Core::RakeTask.new do |t|
      t.verbose = true
    end