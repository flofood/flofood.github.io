#encoding: utf-8
require 'rubygems'
require 'jekyll'
require 'rake'
require 'yaml'
require 'time'

task :blog do
  OptionParser.new.parse!
  ARGV.shift
  title = ARGV.join(' ')

  path = "_posts/2015/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.md"

  if File.exist?(path)
    puts "[WARN] File exists - skipping create"
  else
    File.open(path, "w") do |post|
    #post.puts YAML.dump({'layout' => 'post', 'published' => false, 'title' => title})
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts 'description: ""'
    post.puts "category: Blog"
    post.puts "tags:"
    post.puts "- Change Me"
    post.puts "---"
    post.puts ""
    post.puts "<!--start excerpt-->"
    post.puts ""
    post.puts ""
    post.puts "{{ more }}"
    post.puts ""
    post.puts "{% highlight bash html linenos %}"
    post.puts ""
    post.puts "{% endhighlight %}"
    post.puts ""
    post.puts "<div class=\"figure\">"
    post.puts "<img src=\" \">"
    post.puts "</div>"
    end
  end
  #`subl #{path}`
system ("#{ENV['EDITOR']} _posts/2015/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.md")
  exit 1
end

task :recipes do
  OptionParser.new.parse!
  ARGV.shift
  title = ARGV.join(' ')

  path = "_posts/recipes/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.md"

  if File.exist?(path)
    puts "[WARN] File exists - skipping create"
  else
    File.open(path, "w") do |post|
    #post.puts YAML.dump({'layout' => 'post', 'published' => false, 'title' => title})
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts 'description: ""'
    post.puts "category: recipes"
    post.puts "tags:"
    post.puts "- Change Me"
    post.puts "---"
    post.puts ""
    end
  end
  #`subl #{path}`
system ("#{ENV['EDITOR']} _posts/recipes/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.md")
  exit 1
end

task :wine do
  OptionParser.new.parse!
  ARGV.shift
  title = ARGV.join(' ')

  path = "_posts/wine/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.md"

  if File.exist?(path)
    puts "[WARN] File exists - skipping create"
  else
    File.open(path, "w") do |post|
    #post.puts YAML.dump({'layout' => 'post', 'published' => false, 'title' => title})
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts 'description: ""'
    post.puts "category: wine"
    post.puts "tags:"
    post.puts "- Change Me"
    post.puts "---"
    post.puts ""
    post.puts "Price: £"
    post.puts "Date Purchased:"
    post.puts "Supplier:"
    post.puts "Region:"
    post.puts ""
    post.puts "![](/images/wine/ )"
    end
  end
  #`subl #{path}`
system ("#{ENV['EDITOR']} _posts/wine/#{Date.today}-#{title.downcase.gsub(/[^[:alnum:]]+/, '-')}.md")
  exit 1
end
