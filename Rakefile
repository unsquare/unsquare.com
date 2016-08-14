task default: %w[test]

require 'html/proofer'

desc 'Check for broken links or images'
task :test do
  sh "jekyll build"
  HTML::Proofer.new("./_site").run
end

desc 'Publishing the website via rsync'
task :deploy do
  sh "jekyll build"
  puts 'Publishing your website, silence is golden...'
  user = 'unsquare'
  server = 'unsquare.com'
  path = '/home/unsquare/unsquare.com/'
  sh "rsync -vrzc --delete --exclude-from=excludes.txt _site/ #{user}@#{server}:#{path}"
  puts 'Your website is now published!'
end