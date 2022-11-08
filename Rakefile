namespace :greeting do # <-- combines the tasks :hello and :hola into a parent namespace called :greeting
desc 'outputs hello to the terminal'
  task :hello do
    puts "hello from Rake!"
  end

  desc 'outputs hola to the terminal'
  task :hola do
    puts "hola de Rake!"
  end
end

namespace :db do
  desc 'migrate changes to your database'
  task migrate: :environment do # <-- tells Rake that it needs to run the task :environment before it can execute :migrate
    Student.create_table
  end
# ^^^ creates a table to store our data
  desc 'seed the database with some dummy data'
  task seed: :environment do
    require_relative './db/seeds'
  end
  #^^^ uses the seeds.rb file to fill our table (with instances of the Student class)
end

task :environment do
  require_relative './config/environment'
end
# ^^^ task that runs BEFORE our database migration, which sets up our Student class (in Student.rb)

desc 'drop into the Pry console'
task console: :environment do
  Pry.start
end
# ^^^ starts up the Pry console so we can interact with our class and database without having to run the entire program