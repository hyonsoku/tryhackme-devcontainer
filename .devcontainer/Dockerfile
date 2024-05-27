FROM kalilinux/kali-rolling

RUN apt update && apt install -y openvpn && \
    apt install -y novnc x11vnc

# Configuration for noVNC
RUN  x11vnc -display :0 -autoport -localhost -nopw -bg -xkb -ncache -ncache_cr -quiet -forever
RUN /usr/share/novnc/utils/novnc_proxy --listen 8081 --vnc localhost:5900
RUN systemctl enable ssh --now

EXPOSE 8081/tcp