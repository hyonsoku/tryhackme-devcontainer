FROM kalilinux/kali-rolling

RUN apt-get update && apt-get upgrade -y && \8081
    apt-get install -y \
        kali-linux-headless \
        kali-desktop-gnome \
        novnc x11vnc procps && \
    apt-get autoremove -y && \
    apt-get clean

# Configuration for OpenVPN
COPY *.ovpn /etc/openvpn

# Configuration for noVNC
CMD  x11vnc -display :0 -autoport -localhost -nopw -bg -xkb -ncache -ncache_cr -quiet -forever
CMD /usr/share/novnc/utils/novnc_proxy --listen 8081 --vnc localhost:5900
CMD systemctl enable ssh --now

EXPOSE 8081/tcp