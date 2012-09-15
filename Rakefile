PROJECT_PATH = File.expand_path("..", __FILE__)


task :default => :install

desc "Install/symlink themes for all currently available applications"
task :install do
  Rake::Task["install:alfred"].invoke(true)
  Rake::Task["install:color_theme"].invoke(true)
end

namespace :install do

  desc "Install the Alfred theme"
  task :alfred, [:silent] do |t, args|
    prefs_path = File.expand_path("~/Library/Application Support/Alfred/themes/Themes.plist")
    if `grep -s "<string>Fireballed</string>" "#{prefs_path}"`.strip.size > 0
      puts "Alfred theme already installed" unless args.silent
    else
      `open "#{File.join(PROJECT_PATH, "Fireballed.alfredtheme")}"`
    end
  end

  desc "Install the OS X color picker scheme"
  task :color_theme, [:silent] do |t, args|
    target_path = File.expand_path("~/Library/Colors/Fireballed.clr")
    if File.exists? target_path
      puts "OS X color picker scheme already installed at #{target_path}" unless args.silent
    else
      `ln -s "#{File.join(PROJECT_PATH, "Fireballed.clr")}" #{target_path}`
    end
  end

end
