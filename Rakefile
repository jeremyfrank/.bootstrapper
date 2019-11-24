require 'fileutils'
require 'rake'
require 'erb'

desc 'Bootstrap a new Mac!'
task :install do
  Rake::Task['install:homebrew'].invoke
  Rake::Task['install:asdf'].invoke
  Rake::Task['install:ohmyzsh'].invoke
  Rake::Task['install:composer'].invoke
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
    system 'sh -c "$(git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.7.5)"'

    puts 'Adding asdf to shell...'
    system 'sh -c "$(echo \'\n. $HOME/.asdf/asdf.sh\' >> ~/.bash_profile)"'
    system 'sh -c "$(echo \'\n. $HOME/.asdf/completions/asdf.bash\' >> ~/.bash_profile)"'
  end

  desc 'Installs Oh My Zsh'
  task :ohmyzsh do
    puts 'Installing Oh My Zsh...'
    system 'sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"'
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
