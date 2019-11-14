require 'rake'
require 'erb'

desc 'Bootstrap a new Mac!'
task :install do
  Rake::Task['install:homebrew'].invoke
  Rake::Task['install:asdf'].invoke
  Rake::Task['install:ohmyzsh'].invoke
  sh 'brew bundle'
end

desc 'Installs system requirements'
namespace :install do
  desc 'Installs Homebrew'
  task :homebrew do
    puts 'Installing Homebrew...'
    system '/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"'
  end

  desc 'Installs asdf'
  task :asdf do
    puts 'Installing asdf...'
    system 'git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.7.5'

    puts 'Adding asdf to shell...'
    system 'echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bash_profile'
    system 'echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bash_profile'
  end

  desc 'Installs Oh My Zsh'
  task :ohmyzsh do
    puts 'Installing Oh My Zsh...'
    system 'sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"'
  end
end
