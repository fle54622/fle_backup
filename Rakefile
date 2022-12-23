require "colorize"

task :default do
  system "rake --tasks"
end

desc "backup_template"
task :backup_template do
  print "Enter the name of the directory to be created: "
  d_name = STDIN.gets
  print "Enter the number of backups you wish to create: "
  b_num = STDIN.gets
  ["mkdir #{d_name}",
   "mkdir ./#{d_name.chomp}/main",
   "mkdir ./#{d_name.chomp}/backup"].each do |comm|
    puts comm.cyan
    system comm
  end
  for roop in 1..b_num.to_i
    ["mkdir ./#{d_name.chomp}/backup/backup_#{roop}"].each do |comm|
      puts comm.cyan
      system comm
    end
  end
  exit
end

desc "backup_update"
task :backup_update do
  print "Enter the path of the desired directory: "
  d_pass = STDIN.gets
  dir = "."
  p dir = File.join(dir, "#{d_pass.chomp}/backup/*")
  p b_num = Dir.glob(dir).count
  ["rm -rf #{d_pass.chomp}/backup/backup_#{b_num}"].each do |comm|
    puts comm.cyan
    system comm
  end
  for roop in 1..b_num.to_i - 1
    roop2 = roop - 1
    low = "#{b_num}".to_i - roop
    high = "#{b_num}".to_i - roop2
    ["mv #{d_pass.chomp}/backup/backup_#{low} backup_#{high}",
     "mv backup_#{high} ./#{d_pass.chomp}/backup"].each do |comm|
      puts comm.cyan
      system comm
    end
  end
  ["cp -r #{d_pass.chomp}/main .",
   "mv main backup_1",
   "mv backup_1 ./#{d_pass.chomp}/backup"].each do |comm|
    puts comm.cyan
    system comm
  end
  exit
end

desc "backup_use"
task :backup_use do
  print "Enter the path of the desired directory: "
  d_pass = STDIN.gets
  print "Enter the number of backups you want to use: "
  u_num = STDIN.gets
  dir = "."
  p dir = File.join(dir, "#{d_pass.chomp}/backup/*")
  p b_num = Dir.glob(dir).count
  ["rm -rf #{d_pass.chomp}/main",
   "cp -r ./#{d_pass.chomp}/backup/backup_#{u_num.chomp} .",
   "mv backup_#{u_num.chomp} main",
   "mv main ./#{d_pass.chomp}/"].each do |comm|
    puts comm.cyan
    system comm
  end
end

desc "backup_add"
task :backup_add do
  print "Enter the path of the desired directory: "
  d_pass = STDIN.gets
  print "Enter the number of backups you wish to add: "
  b_add = STDIN.gets
  dir = "."
  p dir = File.join(dir, "#{d_pass.chomp}/backup/*")
  p b_num = Dir.glob(dir).count
  for roop in (b_num.to_i + 1)..(b_num.to_i + b_add.to_i)
    ["mkdir ./#{d_pass.chomp}/backup/backup_#{roop}"].each do |comm|
      puts comm.cyan
      system comm
    end
  end
end

desc "backup_remove"
task :backup_remove do
  print "Enter the path of the desired directory: "
  d_pass = STDIN.gets
  print "Enter the number of backups you want to remove: "
  b_remove = STDIN.gets
  dir = "."
  p dir = File.join(dir, "#{d_pass.chomp}/backup/*")
  p b_num = Dir.glob(dir).count
  for roop in (b_num.to_i - b_remove.to_i + 1)..(b_num.to_i)
    ["rm -rf #{d_pass.chomp}/backup/backup_#{roop}"].each do |comm|
      puts comm.cyan
      system comm
    end
  end
end
