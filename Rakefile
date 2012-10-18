task :create_visc do
  Dir.glob("*.ovpn") do |ovpn_file|
    puts "Starting to configure #{ovpn_file}"
    user = File.basename(ovpn_file, ".ovpn")
    bundle_name = "#{user}.visc"
    FileUtils.rm_r("#{user}.visc", :force => true) if File.exists?("#{user}.visc")
    config_files = Dir.glob("#{user}.*")
    FileUtils.mkdir bundle_name
    FileUtils.cp config_files, bundle_name
    Dir.chdir(bundle_name) do 
      FileUtils.mv "#{user}.conf", "config.conf"
      File.open("config.conf", "a") do |file|
        file.puts "#viscosity dnssupport true"
        file.puts "#viscosity name GS HK Office"
      end
    end
  end
end
