sudo apt update

sudo apt install nginx

sudo apt install -y apache2
sudo a2enmod rewrite
sudo service apache2 restart

sudo apt install -y php php-cli php-fpm php-mysql php-json php-opcache php-mbstring php-xml php-gd php-curl git zip unzip composer

# Server hardening
cat <<EOF >>/etc/apache2/apache2.conf
ServerSignature Off
ServerTokens Prod
TraceEnable off
EOF
sudo service apache2 restart
