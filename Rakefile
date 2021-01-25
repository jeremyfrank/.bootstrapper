require 'fileutils'
require 'rake'
require 'erb'

desc 'Bootstrap a new Mac!'
task :install do
  Rake::Task['install:homebrew'].invoke
  Rake::Task['install:asdf'].invoke
  Rake::Task['install:ohmyzsh'].invoke
  Rake::Task['install:composer'].invoke
end

desc 'Installs system requirements'
namespace :install do
  desc 'Installs Homebrew'
  task :homebrew do
    puts 'Installing Homebrew...'
    system '/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"'
  end

  desc 'Installs asdf'
  task :asdf do
    puts 'Installing asdf...'
    system 'sh -c "$(git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.8.0)"'
  end

  desc 'Installs Oh My Zsh'
  task :ohmyzsh do
    puts 'Installing Oh My Zsh...'
    system 'sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"'
  end

  desc 'Installs Composer'
  task :composer do
    puts 'Installing Composer...'
    FileUtils.chmod_R "u=wrx", "install_composer.sh"
    system 'sh -s "$(install_composer.sh)"'

    puts 'Moving composer.phar file...'
    system 'sh -c "$(mv composer.phar /usr/local/bin/composer)"'
  end

end
