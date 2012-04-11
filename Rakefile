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
  system "jekyll --auto --server"
end

desc "Build site"
task :build => [:haml, :clean] do |task, args|
  system "jekyll"
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
