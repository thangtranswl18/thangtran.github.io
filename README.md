# 🌐 Ads.txt Hosting Site

A simple and efficient GitHub Pages website for hosting ads.txt files to verify authorized digital advertising sellers.

## 📋 Overview

This repository provides a free, reliable solution for hosting ads.txt files using GitHub Pages. Perfect for publishers who need to manage authorized digital advertising sellers across multiple domains.

## ✨ Features

- 🆓 **Free Hosting** - Powered by GitHub Pages
- 📝 **Easy Management** - Simple file-based editing
- 🔄 **Version Control** - Full git history of all changes
- 🌍 **Custom Domain Support** - Use your own domain
- 🔒 **SSL/HTTPS** - Automatic SSL certificates
- ⚡ **Global CDN** - Fast worldwide access
- 📱 **Mobile Support** - app-ads.txt for mobile apps

## 🚀 Quick Start

### 1. Setup Repository

```bash
# Fork or clone this repository
git clone https://github.com/yourusername/ads-txt-site.git
cd ads-txt-site
```

### 2. Configure Your ads.txt

Edit the `ads.txt` file with your authorized sellers:

```
# ads.txt for yourdomain.com
google.com, pub-1234567890123456, DIRECT, f08c47fec0942fa0
facebook.com, 123456789, DIRECT, c3e20eee3f780d68
amazon.com, 3456, DIRECT, 78b21b4b2c94d41c
```

### 3. Enable GitHub Pages

1. Go to **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: **main** / Folder: **/ (root)**
4. Click **Save**

### 4. Access Your ads.txt

Your file will be available at:
- `https://yourusername.github.io/ads-txt-site/ads.txt`
- `https://yourcustomdomain.com/ads.txt` (if custom domain configured)

## 📁 File Structure

```
├── README.md              # Documentation
├── ads.txt               # Main ads.txt file
├── app-ads.txt           # Mobile app ads.txt
├── sellers.json          # Sellers.json (optional)
├── CNAME                 # Custom domain config
└── .github/
    └── workflows/
        └── validate.yml  # Auto-validation (optional)
```

## 🔧 Configuration

### Custom Domain Setup

1. **Create CNAME file:**
   ```
   ads.yourdomain.com
   ```

2. **Configure DNS:**
   ```
   Type: CNAME
   Name: ads
   Value: yourusername.github.io
   TTL: 300
   ```

3. **Enable HTTPS** in repository settings

### ads.txt Format

```
# Format: <Domain>, <Publisher ID>, <Relationship>, <Certification Authority>

# Google AdSense
google.com, pub-XXXXXXXXXXXXXXXX, DIRECT, f08c47fec0942fa0

# Facebook Audience Network  
facebook.com, XXXXXXXXXXXXXXXX, DIRECT, c3e20eee3f780d68

# Amazon Publisher Services
amazon.com, XXXX, DIRECT, 78b21b4b2c94d41c

# Unity Ads
unity.com, XXXXXXX, DIRECT, 96cabb5fbdde37a7

# AppLovin
applovin.com, XXXXXXXXXXXXXXXX, DIRECT

# AdMob (same as AdSense)
google.com, pub-XXXXXXXXXXXXXXXX, DIRECT, f08c47fec0942fa0
```

## 📱 Mobile Apps (app-ads.txt)

For mobile app monetization, create `app-ads.txt`:

```
# app-ads.txt for mobile applications
google.com, pub-XXXXXXXXXXXXXXXX, DIRECT, f08c47fec0942fa0
facebook.com, XXXXXXXXXXXXXXXX, DIRECT, c3e20eee3f780d68
unity.com, XXXXXXX, DIRECT, 96cabb5fbdde37a7
applovin.com, XXXXXXXXXXXXXXXX, DIRECT
```

## 🔄 Updating Files

### Via GitHub Web Interface

1. Navigate to the file (e.g., `ads.txt`)
2. Click the **Edit** button (pencil icon)
3. Make your changes
4. Scroll down and commit changes
5. Changes will be live within minutes

### Via Git Commands

```bash
# Clone repository
git clone https://github.com/yourusername/ads-txt-site.git
cd ads-txt-site

# Edit files
nano ads.txt

# Commit and push changes
git add .
git commit -m "Update ads.txt entries"
git push origin main
```

## ✅ Verification & Testing

### Validation Tools

- [IAB ads.txt Validator](https://iabtechlab.com/ads-txt/)
- [Google ads.txt Guide](https://support.google.com/adsense/answer/7532444)
- [Ads.txt Guru](https://adstxt.guru/)

### Manual Testing

```bash
# Test direct access
curl https://yourdomain.com/ads.txt

# Check HTTP headers
curl -I https://yourdomain.com/ads.txt

# Validate format
curl https://yourdomain.com/ads.txt | head -5
```

## 🛡️ Best Practices

### Security
- ✅ Regularly review and update seller entries
- ✅ Remove unauthorized or inactive sellers
- ✅ Monitor for unauthorized changes
- ✅ Keep backups of working configurations

### Performance
- ✅ Keep file size reasonable (< 100KB)
- ✅ Use comments for organization
- ✅ Remove duplicate entries
- ✅ Test after each update

### Maintenance
- ✅ Set up monitoring alerts
- ✅ Review quarterly
- ✅ Document all changes
- ✅ Test on multiple devices

## 🌐 Multiple Domains

### Option 1: Subdomain Approach
```
ads1.yourdomain.com → GitHub Pages Site 1
ads2.yourdomain.com → GitHub Pages Site 2
```

### Option 2: Redirect Approach
```
yourdomain.com/ads.txt → 301 Redirect → GitHub Pages
```

### Option 3: Multiple Repositories
- Create separate repositories for each domain
- Use different CNAME files
- Manage independently

## 🔍 Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| 404 Error | Check GitHub Pages is enabled |
| SSL Certificate Issues | Enable "Enforce HTTPS" |
| Custom Domain Not Working | Verify DNS configuration |
| Changes Not Reflecting | Wait 5-10 minutes for cache |
| File Not Loading | Check file permissions |

### Debug Commands

```bash
# Check DNS propagation
nslookup ads.yourdomain.com

# Test HTTP response
curl -v https://yourdomain.com/ads.txt

# Check SSL certificate
openssl s_client -connect yourdomain.com:443 -servername yourdomain.com
```

## 📊 Monitoring (Optional)

### GitHub Actions Validation

Create `.github/workflows/validate.yml`:

```yaml
name: Validate ads.txt
on: [push, pull_request]
jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Validate ads.txt format
        run: |
          echo "Validating ads.txt format..."
          # Add your validation logic here
          grep -E "^[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}, .+, (DIRECT|RESELLER), [a-f0-9]{16}$" ads.txt
```

## 📚 Resources

- 📖 [IAB ads.txt Specification](https://iabtechlab.com/ads-txt/)
- 📖 [GitHub Pages Documentation](https://docs.github.com/en/pages)
- 📖 [Google AdSense ads.txt Guide](https://support.google.com/adsense/answer/7532444)
- 📖 [Facebook ads.txt Requirements](https://www.facebook.com/business/help/1701077533414756)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Commit your changes (`git commit -am 'Add some improvement'`)
5. Push to the branch (`git push origin feature/improvement`)
6. Create a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 💬 Support

- 🐛 **Bug Reports**: [GitHub Issues](https://github.com/yourusername/ads-txt-site/issues)
- 💡 **Feature Requests**: [GitHub Discussions](https://github.com/yourusername/ads-txt-site/discussions)
- 📧 **Email**: your-email@domain.com

---

**⚠️ Important**: Replace all placeholder values (`yourusername`, `yourdomain.com`, `XXXXXXXXXXXXXXXX`) with your actual information before using this configuration.

**🔄 Last Updated**: December 2024
