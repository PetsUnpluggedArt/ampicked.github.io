# Ampicked Affiliate Links

## Affiliate Links Tracking

| Provider | Affiliate Link | Status | Review File | CTA Status |
|----------|---|---|---|---|
| SiteGround | `https://www.siteground.com/index.htm?afcode=3e74201a12b5ba9ca32e31cdff01ce74` | ✅ Active | `2026-04-27-siteground-review.md` | ✅ Active CTA |
| WPEngine | [PENDING] | ⏳ Under Review | `2026-04-27-wp-engine-review.md` | 🔲 Placeholder CTA |
| Hostinger | [PENDING] | ⏳ Under Review | `2026-04-27-hostinger-review.md` | 🔲 Placeholder CTA |
| Bluehost | [PENDING] | ⏳ Under Review | `2026-04-27-bluehost-review.md` | 🔲 Placeholder CTA |
| Bluehost Pro | [SHARED] | ⏳ Under Review | `2026-04-27-bluehost-pro-review.md` | 🔲 Placeholder CTA |
| DigitalOcean | [PENDING] | ⏳ Under Review | `2026-04-27-digitalocean-review.md` | 🔲 Placeholder CTA |
| Kinsta | [PENDING] | ⏳ Under Review | `2026-04-27-kinsta-review.md` | 🔲 Placeholder CTA |
| Pressable | [PENDING] | ⏳ Under Review | `2026-04-27-pressable-review.md` | 🔲 Placeholder CTA |
| Linode | [PENDING] | ⏳ Under Review | `2026-04-27-linode-review.md` | 🔲 Placeholder CTA |

## CTA Implementation Status

All 9 review files now have CTAs installed:
- ✅ **1 Active CTA** (SiteGround) - Links to affiliate URL
- 🔲 **8 Placeholder CTAs** (All others) - Shows "Coming Soon - Affiliate Link Pending"

## How to Update When Approved

When an affiliate link is approved:
1. Add the affiliate link to this tracking file
2. Open the corresponding review file (`.md`)
3. Replace the placeholder CTA div with the active CTA button
4. Update the Status and CTA Status columns in this file

### Active CTA Template
```html
<a href="[AFFILIATE_LINK]" style="display: inline-block; background: white; color: #667eea; padding: 14px 35px; border-radius: 5px; text-decoration: none; font-weight: 600; font-size: 1.1em; transition: transform 0.3s ease; transform: translateY(0);" onmouseover="this.style.transform='translateY(-2px)'" onmouseout="this.style.transform='translateY(0)'">
  Get Started with [Provider] →
</a>
```

### Placeholder CTA Template
```html
<div style="background: rgba(255,255,255,0.2); padding: 15px 25px; border-radius: 5px; display: inline-block;">
  <p style="margin: 0; font-size: 0.9em; opacity: 0.85;">Coming Soon - Affiliate Link Pending</p>
</div>
```

## Notes

- All CTAs are styled with gradient background (purple to darker purple)
- Hover effect on active links (slight upward transform)
- CTAs positioned before final navigation links at end of each article
- Both active and pending CTAs include provider-specific messaging and benefits
- Tracking codes included in SiteGround link format for consistency
