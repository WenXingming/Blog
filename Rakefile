# This is a Rakefile, a "Makefile" for Ruby, it's a "定义和执行自动化任务的脚本". You can use it to automate tasks. ——by wxm

# Load rake and any other required gems
require "rubygems"
require 'rake'
require 'yaml'
require 'time'

# Base configuration
SOURCE = "."
CONFIG = {
  'version' => "12.3.2",
  'themes' => File.join(SOURCE, "_includes", "themes"), # 注意: havo no document descripted
  'layouts' => File.join(SOURCE, "_layouts"),
  'posts' => File.join(SOURCE, "_posts"),
  'post_ext' => "md",
  'theme_package_version' => "0.1.0"
}

# 【important】Usage: rake post title="A Title" subtitle="A sub title"
desc "Begin a new post in #{CONFIG['posts']}"
task :post do
  abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])
  title = ENV["title"] || "new-post"
  subtitle = ENV["subtitle"] || "This is a subtitle"
  slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  begin
    date = (ENV['date'] ? Time.parse(ENV['date']) : Time.now).strftime('%Y-%m-%d')
  rescue Exception => e
    puts "Error - date format must be YYYY-MM-DD, please check you typed it correctly!"
    exit -1
  end
  filename = File.join(CONFIG['posts'], "#{date}-#{slug}.#{CONFIG['post_ext']}")
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end

  # 【important】create post file's front-matter. Reference:https://jekyllcn.com/docs/frontmatter/
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts "subtitle: \"#{subtitle.gsub(/-/,' ')}\""
    post.puts "date: #{Time.now.strftime('%Y-%m-%d %H:%M:%S')}"
    post.puts "author: \"WenXingming\""
    post.puts "published: true"
    post.puts "catalog: true"
    post.puts "# header-img: \"{{baseurl}}/img/xxx\""
    post.puts "tags: []"
    post.puts "---"
  end
end # task :post

# #Load custom rake scripts
# Dir['_rake/*.rake'].each { |r| load r }
