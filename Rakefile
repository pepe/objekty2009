namespace :docs do
  desc "Format all txt files with markout."
  task :markout do
    Dir['*.txt'].each do |file|
      system "markout #{file}"
    end
  end
end

