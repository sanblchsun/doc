# doc
create RDP in Debian

apt update && apt -y upgrade
apt purge xrdp
apt install -y xrdp
apt install -y xfce4
apt install -y xfce4-goodies

cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini
echo xfce4-session > ~/.xsession

nano /etc/xrdp/startwm.sh
        !comment these lines to:
        #test -x /etc/X11/Xsession && exec /etc/X11/Xsession
        #exec /bin/sh /etc/X11/Xsession

        !add these lines:
        # xfce
        startxfce4
/etc/init.d/xrdp stop
apt install dbus-x11
/etc/init.d/xrdp start
