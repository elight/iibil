# A sample Guardfile
# More info at https://github.com/guard/guard#readme



# Add files and commands to this file, like the example:
#   watch(%r{file/path}) { `command(s)` }
#
guard 'shell' do
  watch(/(.*).md/) {|m| `keydown slides #{m[0]}` }
  #watch(/(.*).jpg/) {|m| `mv #{m[0]} images` }
  #watch(/(.*).png/) {|m| `mv #{m[0]} images` }
end

# Add files and commands to this file, like the example:
#   watch(%r{file/path}) { `command(s)` }
#
guard 'shell' do
  watch(/(.*).txt/) {|m| `tail #{m[0]}` }
end
