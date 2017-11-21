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
  desc 'Installs Homebrew'
  task :homebrew do
    puts 'Installling Homebrew...'
    system '/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"'
  end

  desc 'Installs RVM and Ruby'
  task :rvm do
    puts 'Installing RVM and Ruby...'
    system 'curl -sSL https://get.rvm.io | bash -s stable --ruby'
  end

  desc 'Installs NVM and Node'
  task :nvm do
    puts 'Installing NVM and Node...'
    system 'curl -o- https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash'
    system 'nvm install node'
    system 'nvm alias default node'
    system 'npm install --global trash-cli' # https://github.com/sindresorhus/trash
  end

  desc 'Installs Oh My Zsh'
  task :ohmyzsh do
    puts 'Installling Oh My Zsh...'
    system 'sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"'
  end

  # shell script below wasn't working properly
  # it was downloading the incorrect version of IE
  desc 'Installs IE VMs for VirtualBox'
  task :ievms do
    puts 'Installing IE VMs...'
    system 'curl -s https://raw.github.com/xdissent/ievms/master/ievms.sh | env IEVMS_VERSIONS="9 10 11 EDGE" bash'
  end
end
