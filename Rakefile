desc "Parse haml layouts"
task :haml do
  print "Parsing Haml layouts..."
  system(%{
    cd _layouts/ &&
    for f in haml/*.haml; do
      o=${f##*/};
      [ -e $f ] && haml $f ${o%.haml}.html;
    done
  })
  puts "done."
end

desc "Launch preview environment"
task :preview => [:haml, :clean] do
  system "jekyll serve --watch --baseurl /"
end

desc "Build site"
task :build => [:haml, :clean, "compass:compile"] do |task, args|
  system "jekyll build"
end

desc "Deploy site"
task :deploy => [:build] do |task, args|
  system "rsync -rv --chmod=Dgo+rx,Fgo+r _site/ ~/Volumes/gabira/httpdocs/"
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
