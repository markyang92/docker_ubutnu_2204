FROM ubuntu_2204:1.0
 
RUN apt update
RUN apt full-upgrade -y
 
RUN apt install -y software-properties-common
RUN add-apt-repository ppa:ubuntu-toolchain-r/test
RUN apt update -y
RUN apt install -y build-essential
 
RUN apt install -y openssh-server
RUN apt install -y lib32stdc++-11-dev lib32gcc-11-dev g++-multilib
RUN sed -i 's#exit 101#exit 0#g' /usr/sbin/policy-rc.d
RUN RUNLEVEL=1 dpkg-reconfigure openssh-server
RUN update-rc.d ssh defaults

RUN echo "root:root" | chpasswd # 초기 root의 비밀번호는 root임(컨테이너에서 바꾸기)

ARG user=jenkins
ARG id_u=1001
ARG id_g=1001
RUN groupadd -g $id_g -o $user && useradd -m -p $user -u $id_u -g $id_g -o -s /bin/bash $user

# user에 sudo 권한 부여하기
RUN usermod -aG sudo $user
RUN echo "${user}:${user}" | chpasswd # user의 초기 비밀번호는 user 컨테이너에서 바꿀 것!
 
WORKDIR /home/$user
CMD /bin/bash

