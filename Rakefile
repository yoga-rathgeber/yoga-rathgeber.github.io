desc "Launch preview environment"
task :preview => [:clean] do
  system "jekyll serve --watch --baseurl /"
end

desc "Build site"
task :build => [:clean, "compass:compile"] do |task, args|
  system "jekyll build"
end

task :clean do
  system "rm -rf _site"
end


namespace :compass do

  desc 'Delete temporary compass files'
  task :clean do
    system "rm -fR css/*"
  end

  desc 'Run the compass watch script'
  task :watch do
    system "compass watch"
  end

  desc 'Compile sass scripts'
  task :compile => [:clean] do
    system "compass compile"
  end

end
