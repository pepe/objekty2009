namespace :docs do
  desc "Format all txt files with markout."
  task :markout do
    Dir['*.txt'].each do |file|
      system "markout #{file}"
    end
  end

  desc "Format all txt files with markout with history"
  task :history_markout do
    Dir['*.txt'].each do |file|
      system "markout -h #{file}"
    end
  end
end

