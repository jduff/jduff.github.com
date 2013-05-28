task :default => :server

desc 'Clean up generated site'
task :clean do
end

desc 'Build site with Jekyll'
task :build => :clean do
  cpid = compass
  jpid = jekyll

  trap_and_kill cpid, jpid
end

desc 'Start server with --auto'
task :server => :clean do
  cpid = compass
  jpid = jekyll('serve --watch')

  trap_and_kill cpid, jpid
end


def jekyll(opts = '')
  fork do
    sh 'jekyll ' + opts
  end
end

def compass(opts = '')
  fork do
    sh 'compass watch'
  end
end

def trap_and_kill(*pids)
  Signal.trap("TERM") do
    pids.each do |pid|
      Process.kill("TERM", pid)
    end
  end

  Signal.trap("INT") do
    pids.each do |pid|
      Process.kill("INT", pid)
    end
  end

  Process.waitall
end
