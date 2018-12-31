# coding: utf-8

# CONFIGURATION VARIABLES (on top of those defined by Jekyll in _config(_deploy).yml)
#

# MANAGING POSTS
# Set the extension for new posts (defaults to .textile, if not set)
#
# $post_ext = ".textile"  # default
# $post_ext = ".md"       # if you prefer markdown
#
# Set the location of new posts (defaults to "_posts/", if not set).
# Please, terminate with a slash:
#
# $post_dir = "_posts/"
#
# --- NO NEED TO TOUCH ANYTHING BELOW THIS LINE ---
#

# Specify default values for variables NOT set by the user

$post_ext ||= ".md"
$post_dir ||= "_posts/recipes/"
#
# Tasks start here
#
puts "Correct syntax for a post is"
puts "rake create_post[date,title,category,content]"
puts "Categorys are blog wine recipes tech"

desc 'Create a post'
task :create_post, [:date, :title, :category, :content] do |t, args|
  if args.title == nil then
    puts "Error! title is empty"
    puts "Usage: create_post[date,title,category,content]"
    puts "DATE and CATEGORY are optional"
    puts "DATE is in the form: YYYY-MM-DD; use nil or empty for today's date"
    puts "CATEGORY is a string; nil or empty for no category"
    exit 1
  end
  if (args.date != nil and args.date != "nil" and args.date != "" and args.date.match(/[0-9]+-[0-9]+-[0-9]+/) == nil) then
    puts "Error: date not understood"
    puts "Usage: create_post[date,title,category,content]"
    puts "DATE and CATEGORY are optional"
    puts "DATE is in the form: YYYY-MM-DD; use nil or the empty string for today's date"
    puts "CATEGORY is a string; nil or empty for no category"
    puts ""

    title = args.title || "title"

    puts "Examples: create_post[\"\",\"#{args.title}\"]"
    puts "          create_post[nil,\"#{args.title}\"]"
    puts "          create_post[,\"#{args.title}\"]"
    puts "          create_post[#{Time.new.strftime("%Y-%m-%d")},\"#{args.title}\"]"
    exit 1
  end

  post_title = args.title
  post_date = (args.date != "" and args.date != "nil") ? args.date : Time.new.strftime("%Y-%m-%d %H:%M:%S %Z")

  # the destination directory is <<category>>/$post_dir, if category is non-nil
  # and the directory exists; $post_dir otherwise (a category tag is added in
  # the post body, in this case)
  post_category = args.category
  if post_category and Dir.exists?(File.join(post_category, $post_dir)) then
    post_dir = File.join(post_category, $post_dir)
    yaml_cat = nil
  else
    post_dir = $post_dir
    yaml_cat = post_category ? "category: #{post_category}\n" : nil
  end

  def slugify (title)
    # strip characters and whitespace to create valid filenames, also lowercase
    return title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  end

  filename = post_date[0..9] + "-" + slugify(post_title) + $post_ext

  # generate a unique filename appending a number
  i = 1
  while File.exists?(post_dir + filename) do
    filename = post_date[0..9] + "-" +
               File.basename(slugify(post_title)) + "-" + i.to_s +
               $post_ext 
    i += 1
  end

  # the condition is not really necessary anymore (since the previous
  # loop ensures the file does not exist)
  if not File.exists?(post_dir + filename) then
    File.open(post_dir + filename, 'w') do |f|
      f.puts "---"
      f.puts "layout: post"
      f.puts "title: \"#{post_title}\""
      f.puts "date: #{post_date}"
      f.puts yaml_cat if yaml_cat != nil
      f.puts "tags:"
      f.puts " - change me"
      f.puts "---"
      f.puts ""
      f.puts "<!--start excerpt-->"
      f.puts ""
      f.puts args.content if args.content != nil
      f.puts ""
      f.puts "{{ more }}"
    end

    puts "Post created under \"#{post_dir}#{filename}\""
## line below removed as it caused errors
    ##sh "open \"#{post_dir}#{filename}\"" if args.content == nil

  else
    puts "A post with the same name already exists. Aborted."
  end
  # puts "You might want to: edit #{$post_dir}#{filename}"
end



