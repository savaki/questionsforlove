require 'erb'
require 'yaml'

class Template
  attr_reader :template, :sets

  def initialize(template_file, questions_file)
    @template = File.read(template_file)
    @sets     = YAML.load(File.read(questions_file))
  end

  def render
    ERB.new(template).result(binding)
  end
end

namespace :render do
  desc 'render love.html from template'
  task :closeness do
    template = Template.new 'resources/questions/template.html.erb', 'resources/questions/closeness.yml'
    File.open('resources/public/index.html', 'w') do |io|
      io.puts template.render
    end
  end

  desc 'render smalltalk.html from template'
  task :smalltalk do
    template = Template.new 'resources/questions/template.html.erb', 'resources/questions/smalltalk.yml'
    File.open('resources/public/smalltalk.html', 'w') do |io|
      io.puts template.render
    end
  end

  desc 'render all templates'
  task :all => [:closeness, :smalltalk]
end