# okd_dns
dns config files for local okd dns domain

Network Details:

Virtual Box host only network #3

192.168.56.0/24


yum install -y bind bind-utils

cp /etc/named.conf /root/named.conf.origin

cp -f /root/okd_dns/named.conf /etc

cp /root/okd_dns/forward.okd.local /var/named

cp /root/okd_dns/reverse.okd.local /var/named

named-checkconf okd.local /etc/named.conf

named-checkzone okd.local /var/named/forward.okd.local

named-checkzone okd.local /var/named/forward.okd.local

systemctl enable named

systemctl start named

firewall-cmd --permanent --add-port=53/tcp;firewall-cmd --permanent --add-port=53/udp

firewall-cmd --reload

