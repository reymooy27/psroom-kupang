# 📊 GOOGLE ANALYTICS SETUP GUIDE

## PS Room Kupang - Analytics Implementation

---

## 1️⃣ **BUAT GOOGLE ANALYTICS ACCOUNT**

### Step 1: Sign Up
1. Buka https://analytics.google.com/
2. Login dengan Google account
3. Klik **"Start measuring"**
4. Account name: `PS Room Kupang`
5. Klik **Next**

### Step 2: Property Setup
- Property name: `PS Room Kupang Website`
- Reporting time zone: `Indonesia (Jakarta)`
- Currency: `Indonesian Rupiah (IDR)`
- Klik **Next**

### Step 3: Business Info
- Business size: `1-10 employees`
- Industry category: `Games & Recreation` → `Video Games`
- Business goals: Centang semua yang relevan
  - ✅ Generate leads
  - ✅ Drive traffic to website
  - ✅ Increase engagement
- Klik **Create**

### Step 4: Accept Terms
- Accept Google Analytics Terms
- Accept Data Processing Terms

---

## 2️⃣ **DAPATKAN MEASUREMENT ID**

Setelah create, kamu dapat:
- **Measurement ID:** `G-XXXXXXXXXX`
- **Google Tag:** Script JavaScript

---

## 3️⃣ **IMPLEMENTASI DI WEBSITE**

### Copy Script Ini:

```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Paste di `<head>` Website:

Buka file `index.html`, cari:
```html
<head>
    <meta charset="UTF-8">
```

Paste script Google Analytics **setelah** meta tags SEO, **sebelum** Google Fonts:

```html
<head>
    <meta charset="UTF-8">
    
    <!-- ... SEO Meta Tags ... -->
    
    <!-- Google Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
      gtag('config', 'G-XXXXXXXXXX');
    </script>
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
```

---

## 4️⃣ **TRACKING EVENTS (OPSIONAL)**

### Track Button Clicks:

Tambahkan ini sebelum `</body>`:

```html
<!-- Track Booking Button Clicks -->
<script>
    // Track booking form submission
    document.getElementById('bookingForm').addEventListener('submit', function() {
        gtag('event', 'booking_submit', {
            'event_category': 'conversion',
            'event_label': 'Booking Form Submitted'
        });
    });
    
    // Track CTA button clicks
    document.querySelectorAll('.cta-btn, .hero-btn').forEach(btn => {
        btn.addEventListener('click', function() {
            gtag('event', 'cta_click', {
                'event_category': 'engagement',
                'event_label': this.textContent.trim()
            });
        });
    });
    
    // Track phone number clicks
    document.querySelectorAll('a[href^="https://wa.me"]').forEach(link => {
        link.addEventListener('click', function() {
            gtag('event', 'whatsapp_click', {
                'event_category': 'contact',
                'event_label': 'WhatsApp Click'
            });
        });
    });
    
    // Track social media clicks
    document.querySelectorAll('.social-links a').forEach(link => {
        link.addEventListener('click', function() {
            gtag('event', 'social_click', {
                'event_category': 'social',
                'event_label': link.href
            });
        });
    });
</script>
```

---

## 5️⃣ **VERIFY INSTALLATION**

### Cara Cek:

1. **Real-Time Report:**
   - Buka Google Analytics
   - Reports → Realtime
   - Buka website di browser lain
   - Harus muncul 1 active user

2. **Google Tag Assistant:**
   - Install Chrome extension: [Tag Assistant](https://chrome.google.com/webstore/detail/tag-assistant-by-google/kejbdjndbnbjgmefkgdddjlbokphdefk)
   - Buka website
   - Extension akan show GA4 tag aktif

3. **DebugView:**
   - Admin → DebugView
   - Enable preview mode di browser
   - Events akan muncul real-time

---

## 6️⃣ **METRICS YANG PENTING**

### Untuk Rental PS4:

| Metric | Kenapa Penting | Target |
|--------|----------------|--------|
| **Users** | Total visitor | 100+/bulan |
| **Sessions** | Total visits | 200+/bulan |
| **Avg. Engagement Time** | Berapa lama di website | >1 menit |
| **Bounce Rate** | Yang langsung keluar | <50% |
| **Traffic Source** | Dari mana visitor (Google, IG, WA) | - |
| **Top Pages** | Section paling banyak dilihat | - |
| **Events** | Button clicks, form submits | 20+/bulan |
| **Conversions** | Booking form submit | 10+/bulan |

---

## 7️⃣ **SET UP CONVERSIONS**

### Define Key Events:

1. **Booking Form Submit:**
   - Admin → Events → Mark as conversion
   - Event: `booking_submit`

2. **WhatsApp Click:**
   - Event: `whatsapp_click`
   - Mark as conversion

3. **Phone Call:**
   - Event: `phone_click`
   - Mark as conversion

---

## 8️⃣ **CUSTOM REPORTS**

### Buat Report Ini:

#### **A. Traffic Overview (Mingguan)**
- Dimensions: Date, Source/Medium
- Metrics: Users, Sessions, Engagement time
- Filter: Last 7 days

#### **B. Conversion Report**
- Dimensions: Event name, Page path
- Metrics: Event count, Conversions
- Filter: Conversion events only

#### **C. Geographic Report**
- Dimensions: City, Region
- Metrics: Users, Sessions
- Filter: Indonesia → Nusa Tenggara Timur → Kupang

---

## 9️⃣ **INTEGRASI LAINNYA**

### Google Search Console:
1. Buka https://search.google.com/search-console
2. Add property: `https://reymooy27.github.io/psroom-kupang/`
3. Verify dengan DNS atau HTML file
4. Link dengan Google Analytics

### Google My Business:
1. Buka https://www.google.com/business/
2. Add business: PS Room Kupang
3. Add address, phone, hours
4. Add website URL
5. Verify dengan postcard/phone

---

## 🔟 **PRIVACY & COMPLIANCE**

### Cookie Notice (Optional):

Tambahkan sebelum `</body>`:

```html
<!-- Cookie Notice -->
<div id="cookie-notice" style="position:fixed;bottom:0;left:0;right:0;background:#00439c;color:white;padding:1rem;text-align:center;z-index:9999;display:none;">
    🍪 Website ini menggunakan cookies untuk analisis traffic. 
    <button onclick="document.getElementById('cookie-notice').style.display='none'" 
            style="background:#00b08f;color:white;border:none;padding:0.5rem 1rem;margin-left:1rem;cursor:pointer;border-radius:5px;">
        OK
    </button>
</div>

<script>
    // Show cookie notice
    if(!localStorage.getItem('cookieAccepted')) {
        document.getElementById('cookie-notice').style.display = 'block';
    }
    
    // Hide on accept
    document.querySelector('#cookie-notice button').addEventListener('click', function() {
        localStorage.setItem('cookieAccepted', 'true');
        document.getElementById('cookie-notice').style.display = 'none';
    });
</script>
```

---

## 📈 **MONITORING SCHEDULE**

| Frequency | Action |
|-----------|--------|
| **Daily** | Check real-time users |
| **Weekly** | Review traffic sources, top pages |
| **Monthly** | Analyze conversions, set goals |
| **Quarterly** | Optimize based on data |

---

## 🎯 **KPI TARGET (3 Bulan)**

| Metric | Month 1 | Month 2 | Month 3 |
|--------|---------|---------|---------|
| Users | 100 | 300 | 500 |
| Sessions | 200 | 600 | 1000 |
| Booking Clicks | 10 | 30 | 50 |
| WhatsApp Clicks | 20 | 50 | 100 |
| Avg. Time | 30s | 1m | 2m |

---

**Last Updated:** 2026-06-06  
**For:** PS Room Kupang
