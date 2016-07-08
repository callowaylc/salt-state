#!/usr/bin/env ruby
# callowaylc@gmail
# includes individual tasks

## tasks ########################################

desc "sync to remote environment"
task :sync, [ :remote ] do | t, arguments |
  command  %{
    # below isnt working in rake context.. falling back
    # to ruby solution
    #path=`pwd`
    #repository=${path/$HOME/\~}
    repository="#{ home.sub ENV['HOME'], '~' }"
    fsync ./ #{ arguments[:remote] }:$repository \
      > /tmp/sync.`basename $repository`.log 2>&1 &
  }
end

## methods ######################################

private def command bash
  IO.popen bash do | io |
    while (char = io.getc) do
      print char
    end
  end
end

private def name
  'salt-master-0'
end

private def home
  File.dirname  __FILE__
end