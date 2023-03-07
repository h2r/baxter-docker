task :build do
  sh "docker build . --build-arg hostuid=$(id -u) --build-arg hostgid=$(id -g) --build-arg hostuser=$(whoami) --build-arg hostgroup=$(whoami) --tag baxter:ente --build-arg hostname=$(hostname) --build-arg i2cgid=$(getent group i2c | cut -d: -f3)  --build-arg dialoutgid=$(getent group dialout | cut -d: -f3)  --build-arg videogid=$(getent group video | cut -d: -f3)"
end

task :create do
  sh "docker stop baxter || true"
  sh "docker rm baxter || true"
  sh "docker create -i -t --name baxter --network=host --privileged --volume /home/$USER/catkin_ws:/home/$USER/catkin_ws baxter:ente"
end

task :start do
  sh "docker start --attach -i baxter"
end
