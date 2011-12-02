!SLIDE bullets incremental

# 2: Enhance Bundler's barebones templates

* Bundler left out some important things
* `README.rdoc`
* `.rvmrc` 
* `gem_tasks`



!SLIDE code evensmaller

# `README.rdoc`

    = MyGem

    MyGem does stuff like:
    * foobar
    * snafu

    == Installation

    gem install my_gem

    == Getting Started

    == License

    MyGem is licensed under the MIT License with one addition: 
      The Software shall be used for Good, not Evil.
      
      
!SLIDE commandline incremental

# `.rvmrc`

    $ rvm use ree@my_gem --rvmrc --create
      #-# this will let developers get up and running
      #-# also specifies the ruby version you are targeting
      
      
!SLIDE code small

# `gem_tasks` makes tasks manageable

    @@@ ruby
    # create a directory named `gem_tasks`
    # then add this to `Rakefile`
    Dir['gem_tasks/**/*.rake'].each { |rake| load rake }
    
    # now you can add gem_tasks/some_task.rake for each task