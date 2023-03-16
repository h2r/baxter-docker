task :build do
  sh "docker build . --build-arg hostuid=$(id -u) --build-arg hostgid=$(id -g) --build-arg hostuser=$(whoami) --build-arg hostgroup=$(whoami) --tag baxter --build-arg hostname=$(hostname)"
end

task :create do
  sh "docker stop baxter || true"
  sh "docker rm baxter || true"
  #  sh "docker create -i -t --name baxter --network=host --privileged baxter -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY -h $HOSTNAME -v $HOME/.Xauthority:/home/$USER/.Xauthority"
   sh "docker create -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY -v $HOME/.Xauthority:/home/$USER/.Xauthority -i -t --name baxter --network=host --privileged baxter "
end

task :start do
  sh "docker start --attach -i baxter"
end
