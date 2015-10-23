require 'rake'
require 'erb'

desc 'Bootstrap a new Mac!'
task :install do
  Rake::Task['install:homebrew'].invoke
  Rake::Task['install:rvm'].invoke
  Rake::Task['install:nvm'].invoke
  Rake::Task['install:ohmyzsh'].invoke
  sh 'brew bundle'
  Rake::Task['install:ievms'].invoke
end

desc 'Installs system requirements'
namespace :install do
  desc 'Update or install Homebrew'
  task :homebrew do
    puts 'Installling Homebrew...'
    system 'ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"'
  end

  desc 'Installs RVM and Ruby'
  task :rvm do
    puts 'Installing RVM and Ruby...'
    system 'curl -sSL https://get.rvm.io | bash -s stable --ruby'
  end

  desc 'Installs NVM'
  task :nvm do
    puts 'Installing NVM and Node...'
    system 'curl -o- https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash'
    system 'nvm install stable'
    system 'nvm alias default stable'
  end

  desc 'Installs oh-my-zsh'
  task :ohmyzsh do
    puts 'Installling oh-my-zsh...'
    system 'curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh'
  end

  # shell script below wasn't working properly
  # it was downloading the incorrect version of IE
  desc 'Installs IE VMs for VirtualBox'
  task :ievms do
    puts 'Installing IE VMs...'
    system 'curl -s https://raw.github.com/xdissent/ievms/master/ievms.sh | env IEVMS_VERSIONS="9 10 11 EDGE" bash'
  end
end
