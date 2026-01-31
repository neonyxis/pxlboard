# PXLBoard v12h

**A Modern, Multi-Database PHP Imageboard System**

PXLBoard is a full-featured imageboard platform with support for multiple database backends, modern PHP compatibility, and extensive customization options.

## ✨ What's New in v12h

### 🗄️ Multi-Database Support
- **FlatFile (JSON)**: Simple, zero-config file-based storage
- **SQLite**: Lightweight SQL database with excellent performance
- **MySQL/MariaDB**: Enterprise-grade database for high-traffic sites

### 🚀 PHP 8.3/8.4 Full Compatibility
- All deprecation warnings resolved
- Optimized for PHP 8.3+ performance features
- JIT compilation support
- Modern type safety improvements

### 🐛 Critical Bug Fixes
- Fixed `htmlspecialchars()` null parameter warnings
- Improved error handling across all database backends
- Enhanced type safety in search operations

### 📚 Comprehensive Documentation
- Multi-database migration guide
- PHP 8.3/8.4 compatibility documentation
- Step-by-step upgrade instructions
- Performance optimization guides

## 📋 Features

### Core Features
- **Image Gallery**: Upload, organize, and display images
- **Tagging System**: Categorize content with tags and aliases
- **Boards System**: Create discussion boards with threads and replies
- **User System**: Registration, profiles, authentication, and roles
- **Forums**: Traditional forum with categories and topics
- **Wiki**: Collaborative documentation with revision history
- **Blogs**: Personal blog posts with comments
- **TGP (Thumbnail Gallery Posts)**: Social image sharing with likes
- **Channels**: Organized content channels
- **Admin Panel**: Comprehensive site administration

### Technical Features
- **Multi-Database**: Choose between FlatFile, SQLite, or MySQL
- **RESTful API**: JSON API for external integrations
- **Theme System**: Multiple built-in themes (Default, Dark, Vichan, DPBooru)
- **Image Grabber**: Auto-import from external sources
- **Moderation Tools**: Content moderation and user management
- **RBAC**: Role-based access control
- **Notifications**: User notification system
- **Search**: Full-text search across content
- **Caching**: Built-in caching for performance
- **Responsive**: Mobile-friendly design

## 🚀 Quick Start

### Requirements
- PHP 7.4+ (PHP 8.3+ recommended)
- Web server (Apache/Nginx)
- For MySQL: MySQL 5.7+ or MariaDB 10.3+
- PHP Extensions: PDO, GD, mbstring
- Optional: SQLite extension for SQLite support

### Installation (5 Minutes)

#### 1. Download & Extract
```bash
cd /var/www/html
wget https://github.com/yourrepo/pxlboard/releases/download/v12h/PXLBoard_v12h.zip
unzip PXLBoard_v12h.zip
mv PXLBoard_v12h pxlboard
cd pxlboard
```

#### 2. Set Permissions
```bash
chmod 755 -R .
chmod 777 data
chmod 777 uploads
```

#### 3. Configure Web Server

**Apache (.htaccess included)**:
```apache
# .htaccess is included and should work automatically
# If needed, enable mod_rewrite:
sudo a2enmod rewrite
sudo systemctl restart apache2
```

**Nginx**:
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /var/www/html/pxlboard;
    index index.php;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }

    location ~* \.(jpg|jpeg|png|gif|webp|css|js)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    location /data {
        deny all;
    }
}
```

#### 4. Run Installer
Visit: `http://yourdomain.com/pxlboard/`

You'll be automatically redirected to the installer where you can:
1. Configure site settings
2. Choose database type (FlatFile, SQLite, or MySQL)
3. Create admin account
4. Complete installation

#### 5. Login & Configure
- Default login: admin / (your chosen password)
- Visit Admin Panel to configure themes, settings, and features

## 📊 Database Comparison

| Feature | FlatFile | SQLite | MySQL |
|---------|----------|--------|-------|
| Setup Time | 0 min | 0 min | 5 min |
| Max Images | ~1,000 | ~10,000 | Unlimited |
| Performance | Good | Better | Best |
| Scalability | Low | Medium | High |
| Hosting Req. | Basic | Basic | Database Server |
| Backup | Copy folder | Copy file | SQL dump |
| Best For | Small sites | Medium sites | Large sites |

**Recommendation**:
- **Start with FlatFile**: Zero setup, perfect for testing
- **Upgrade to SQLite**: When you hit 500+ images
- **Move to MySQL**: For 10,000+ images or high traffic

## 🔄 Upgrading from v12g

### Quick Upgrade (5 Minutes)
```bash
# 1. Backup
cp -r pxlboard pxlboard_backup
tar -czf pxlboard_data_backup.tar.gz pxlboard/data

# 2. Download v12h
wget https://github.com/yourrepo/pxlboard/releases/download/v12h/PXLBoard_v12h.zip

# 3. Preserve data
cd pxlboard
mv data data_preserve
mv uploads uploads_preserve

# 4. Replace files
cd ..
rm -rf pxlboard/*
unzip PXLBoard_v12h.zip -d pxlboard/
cd pxlboard

# 5. Restore data
rm -rf data uploads
mv data_preserve data
mv uploads_preserve uploads

# 6. Test
# Visit your site - should work immediately!
```

See [UPGRADE_v12g_to_v12h.md](UPGRADE_v12g_to_v12h.md) for detailed instructions.

## 📖 Documentation

### For Users
- [Installation Guide](INSTALLATION_GUIDE.md) - Detailed setup instructions
- [User Guide](USER_GUIDE.md) - How to use PXLBoard
- [Theme Customization](THEME_GUIDE.md) - Customize appearance

### For Administrators
- [Admin Guide](ADMIN_GUIDE.md) - Site administration
- [Database Migration](DATABASE_MIGRATION_GUIDE.md) - Switch database backends
- [Performance Optimization](PERFORMANCE_GUIDE.md) - Speed up your site
- [Backup & Restore](BACKUP_GUIDE.md) - Data protection

### For Developers
- [API Documentation](API_DOCUMENTATION.md) - RESTful API reference
- [Theme Development](THEME_DEVELOPMENT.md) - Create custom themes
- [Plugin Development](PLUGIN_DEVELOPMENT.md) - Extend functionality
- [Contributing](CONTRIBUTING.md) - How to contribute

### Technical Guides
- [PHP 8.3/8.4 Compatibility](PHP_8_COMPATIBILITY.md) - PHP upgrade guide
- [Upgrade Guide v12g→v12h](UPGRADE_v12g_to_v12h.md) - Version upgrade
- [Troubleshooting](TROUBLESHOOTING.md) - Common issues & solutions

## 🎨 Themes

PXLBoard includes 4 built-in themes:

### Default
Clean, modern design with light colors
- Best for: General purpose sites
- Colors: Blue and white
- Style: Professional

### Dark
Eye-friendly dark theme
- Best for: Night viewing
- Colors: Dark grays with blue accents
- Style: Minimal

### Vichan
Inspired by popular imageboards
- Best for: Traditional imageboard feel
- Colors: Dark with retro styling
- Style: Classic

### DPBooru
Derpibooru-inspired design
- Best for: Media galleries
- Colors: Colorful and vibrant
- Style: Modern booru

Change themes in: Admin Panel → Settings → Theme

## 🔧 Configuration

### Basic Configuration
Edit `/config/config.php` for:
- Site name and URL
- Upload limits
- Timezone
- Error reporting
- Security settings

### Database Configuration
Edit `/data/db_config.json` for:
- Database type selection
- Connection parameters
- Table prefix (MySQL)

### Advanced Configuration
- SMTP settings for email
- Image grabber sources
- Moderation settings
- API configuration

## 🔌 Extensions & Integration

### Image Grabber
Auto-import images from external sources:
- Booru sites
- RSS feeds
- Social media
- Custom sources

Configure in: Admin Panel → Image Grabber

### API Access
RESTful API at `/api/`:
- GET `/api/images` - List images
- GET `/api/image/{id}` - Get image
- POST `/api/upload` - Upload image
- And more...

See [API_DOCUMENTATION.md](API_DOCUMENTATION.md) for full reference.

## 📱 Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Mobile)

## 🔒 Security

PXLBoard includes:
- Password hashing (bcrypt/Argon2)
- CSRF protection
- XSS prevention
- SQL injection prevention (prepared statements)
- File upload validation
- Role-based access control
- Session security

See [SECURITY.md](SECURITY.md) for security best practices.

## 🐛 Troubleshooting

### Common Issues

**Site shows blank page**:
```bash
# Enable error reporting
tail -f /var/log/apache2/error.log
# Check PHP errors
```

**Upload not working**:
```bash
# Check permissions
chmod 777 uploads
# Check PHP upload limits
php -i | grep upload_max_filesize
```

**Database connection error**:
```bash
# Check db_config.json
cat data/db_config.json
# Test database connection
php test_db.php
```

See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for more solutions.

## 📊 Performance Tips

1. **Use OPcache** (built into PHP 8.3):
   ```ini
   opcache.enable=1
   opcache.memory_consumption=128
   ```

2. **Upgrade Database** (if needed):
   - Start: FlatFile
   - Grow: SQLite (1000+ images)
   - Scale: MySQL (10,000+ images)

3. **Enable Gzip Compression**:
   ```apache
   <IfModule mod_deflate.c>
       AddOutputFilterByType DEFLATE text/html text/css text/javascript
   </IfModule>
   ```

4. **Use CDN** for uploads (optional)

5. **Set up Caching** (Redis/Memcached)

See [PERFORMANCE_GUIDE.md](PERFORMANCE_GUIDE.md) for detailed optimization.

## 🤝 Contributing

We welcome contributions!

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📜 License

PXLBoard is open source software licensed under the MIT License.
See [LICENSE](LICENSE) for details.

## 🙏 Credits

### Built With
- PHP 8.3+
- Bootstrap 5
- Font Awesome/Bootstrap Icons
- TinyMCE (editor)
- And many other open source libraries

### Special Thanks
- PXLBoard community
- Contributors
- Beta testers
- Issue reporters

## 📞 Support

### Community Support
- GitHub Issues: [Report bugs](https://github.com/yourrepo/pxlboard/issues)
- Forums: [Community discussion](https://forums.pxlboard.com)
- Discord: [Join chat](https://discord.gg/pxlboard)

### Professional Support
- Email: support@pxlboard.com
- Documentation: https://docs.pxlboard.com

## 🗺️ Roadmap

### v12i (Next Release)
- [ ] Theme customization UI
- [ ] Database import wizard
- [ ] Advanced caching layer
- [ ] REST API v2
- [ ] WebSocket support

### Future Plans
- [ ] Mobile app
- [ ] Federation support
- [ ] AI-powered tagging
- [ ] Video support
- [ ] Advanced search

See [ROADMAP.md](ROADMAP.md) for full roadmap.

## ⚡ Quick Links

- **Installation**: [INSTALLATION_GUIDE.md](INSTALLATION_GUIDE.md)
- **Upgrade**: [UPGRADE_v12g_to_v12h.md](UPGRADE_v12g_to_v12h.md)
- **Database**: [DATABASE_MIGRATION_GUIDE.md](DATABASE_MIGRATION_GUIDE.md)
- **PHP 8.3+**: [PHP_8_COMPATIBILITY.md](PHP_8_COMPATIBILITY.md)
- **Changelog**: [CHANGELOG_v12h.md](CHANGELOG_v12h.md)
- **API Docs**: [API_DOCUMENTATION.md](API_DOCUMENTATION.md)

---

**Version**: 12h  
**Release Date**: January 2026  
**PHP Required**: 7.4+ (8.3+ recommended)  
**Status**: Production Ready ✅

Made with ❤️ by the PXLBoard Team
