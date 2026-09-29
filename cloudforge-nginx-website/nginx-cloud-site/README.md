# CloudForge Nginx Website

## Structure
cloudforge/
├── html/
│   ├── index.html
│   └── assets/
│       ├── css/style.css
│       ├── js/app.js
│       └── images/
└── nginx/
    └── cloudforge.conf

## Ubuntu/Debian deployment

sudo mkdir -p /var/www/cloudforge
sudo cp -r html /var/www/cloudforge/

sudo cp nginx/cloudforge.conf /etc/nginx/sites-available/cloudforge
sudo ln -s /etc/nginx/sites-available/cloudforge /etc/nginx/sites-enabled/cloudforge

sudo nginx -t
sudo systemctl reload nginx

Open:
http://SERVER_IP/

## Ownership
sudo chown -R www-data:www-data /var/www/cloudforge
sudo find /var/www/cloudforge -type d -exec chmod 755 {} \;
sudo find /var/www/cloudforge -type f -exec chmod 644 {} \;

## Troubleshooting
sudo nginx -t
sudo systemctl status nginx
sudo tail -f /var/log/nginx/cloudforge_error.log
sudo tail -f /var/log/nginx/cloudforge_access.log
sudo nginx -T
END ****
