# PXLBoard

A lightweight, flat-file PHP imageboard system designed for shared hosting environments.

## Features

- **Flat-File Storage** - No database required, all data stored in JSON files
- **User System** - Registration, login, and user profiles
- **Image Upload** - Support for JPG, PNG, GIF, and WebP
- **Tagging System** - Organize images with tags
- **Comments** - Users can comment on images
- **Search** - Search images by title, description, or tags
- **SMTP Support** - Email notifications and verification
- **Themes** - Multiple themes (Default and Dark mode included)
- **Admin Panel** - Manage settings, users, and content
- **Responsive** - Mobile-friendly design using Bootstrap 5

## Requirements

- PHP 7.4 or higher
- GD Library (for image processing)
- Apache with mod_rewrite (recommended)

## Installation

1. **Extract the files** to your web server directory

2. **Set permissions** (if on Linux/Unix):
   ```bash
   chmod 755 -R .
   chmod 777 -R data/
   chmod 777 -R uploads/
   ```

3. **Access the installation page**:
   Navigate to `http://yourdomain.com/` in your web browser

4. **Complete the installation wizard**:
   - Enter your site details
   - Create an admin account
   - Configure SMTP (optional)

5. **Done!** You can now log in and start uploading images

## Configuration

After installation, you can modify settings through the Admin Panel:

- Go to your site and log in with your admin account
- Click on "Admin Panel" in the user menu
- Navigate to the "Settings" tab

### SMTP Configuration

To enable email notifications:

1. Go to Admin Panel → Settings → SMTP Settings
2. Check "Enable SMTP"
3. Enter your SMTP server details:
   - Host: e.g., `smtp.gmail.com`
   - Port: Usually `587` for TLS
   - Username: Your email address
   - Password: Your email password or app-specific password
   - From Email: The email address to send from

### Themes

PXLBoard includes two themes:
- **Default** - Clean, modern light theme
- **Dark Mode** - Easy on the eyes dark theme

Users can switch themes from the navigation menu.

## Directory Structure

```
pxlboard/
├── config/          # Configuration files
├── data/            # Flat-file database (auto-created)
├── includes/        # Core PHP files
├── pages/           # Page controllers
├── templates/       # HTML templates
├── themes/          # Theme files
├── uploads/         # Uploaded images (auto-created)
├── index.php        # Main entry point
└── .htaccess        # Apache configuration
```

## Security Notes

1. The `data/` directory is protected by `.htaccess` to prevent direct access
2. User passwords are hashed using PHP's password_hash()
3. File uploads are validated and sanitized
4. SQL injection is not a concern (no database)
5. Consider enabling HTTPS for production use

## Troubleshooting

### "Permission denied" errors
Ensure the web server has write permissions to `data/` and `uploads/` directories:
```bash
chmod 777 -R data/
chmod 777 -R uploads/
```

### Images not uploading
1. Check PHP upload limits in `.htaccess` or `php.ini`
2. Verify the GD library is installed: `php -m | grep gd`
3. Ensure `uploads/` directory exists and is writable

### Email not sending
1. Verify SMTP settings in Admin Panel
2. Check if your hosting provider allows SMTP connections
3. For Gmail, you may need to enable "Less secure app access" or use an app-specific password

## Customization

### Creating a New Theme

1. Create a new directory in `themes/` (e.g., `themes/mytheme/`)
2. Add a `style.css` file with your custom styles
3. Create a `theme.json` file:
   ```json
   {
       "name": "mytheme",
       "display_name": "My Theme",
       "description": "My custom theme",
       "author": "Your Name",
       "version": "1.0.0"
   }
   ```
4. The theme will automatically appear in the theme selector

### Modifying Upload Limits

Edit `.htaccess` or Admin Panel settings to change:
- Maximum file size
- Allowed file types
- Thumbnail dimensions (in `config/config.php`)

## Support

For issues, feature requests, or contributions:
- Report issues on GitHub
- Check the documentation
- Contact the admin at your site's admin email

## License

PXLBoard is released under the MIT License.

## Credits

Built with:
- PHP
- Bootstrap 5
- Inspired by Philomena imageboard software

---

**Version:** 1.0.0
**Author:** PXLBoard Team
