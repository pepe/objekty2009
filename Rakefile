require 'markout'
desc "Format all txt files with markout with history"
task :default => 'docs:history_markout'

namespace :docs do
  desc "Format all txt files with markout to html."
  task :markout do
    Dir['*.txt'].each do |file|
      Markout::Output.new(file, {:output => 'html'}).export(true)
      puts 'Exported fast: ' + file + ' to .html'
    end
  end

  desc "Format all txt files with markout to pdf."
  task :markout_pdf do
    Dir['*.txt'].each do |file|
      Markout::Output.new(file, {:output => 'pdf'}).export(true)
      puts 'Exported fast: ' + file + ' to .pdf'
    end
  end

  desc "Format all txt files with markout with history"
  task :history_markout do
    Dir['*.txt'].each do |file|
      begin
        Markout::Output.new(file, {:output => 'html', :history => true}).export(true)
      rescue
        if file == 'index.txt'
          Markout::Output.new(file, {:output => 'html'}).export(true)
          puts 'Exported fast: ' + file + ' to .html'
        else
          puts 'Have you added ' + file + ' to repo? Cos am dying here!'
        end
      else
        puts 'Exported fast: ' + file + ' to .html'
      end
    end
  end

  desc "Clean up"
  task :clean do
    Dir['html/*.html'].each do |file|
      FileUtils.rm(file)
      puts "Removed " + file
    end
  end

  desc "Refresh index"
  task :refresh_index do
    File.open('index.txt', 'wb') do |index|
      index << "# All files\n\n"
      Dir['*.txt'].each do |file|
        next if file == 'index.txt'
        title = file.split('.').first
        index << "* [#{title.capitalize}](#{title}.html)\n\n"
      end
    end
    puts "Index refreshed. Don't forget to run me after adding txt file!"
  end
end

