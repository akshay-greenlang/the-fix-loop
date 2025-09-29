# Beehiiv Email Template Test Checklist
## The Fix Loop - Micro-Autopsy Newsletter

---

## Pre-Send Validation Checklist

### 1. Size Optimization ⚖️
- [ ] **Total HTML size < 90KB** (target: stay under 90KB for safety margin)
- [ ] **Absolute maximum 102KB** (Beehiiv hard limit)
- [ ] **All HTML comments removed** (saves 2-3KB)
- [ ] **Whitespace minimized** between tags
- [ ] **Inline CSS consolidated** where possible

**Size Check Command:**
```bash
# Check file size in KB
ls -lh micro-autopsy-beehiiv.html | awk '{print $5}'
```

### 2. Content Structure ✍️
- [ ] **Word count: 500-700 words** total
- [ ] **Hook: 20-40 words**
- [ ] **Failure Snapshot: 60-100 words**
- [ ] **FAILSAFE Summary: 90-130 words**
- [ ] **Fix Steps: 200-280 words** (3-7 numbered steps)
- [ ] **Checklist/Asset: 40-120 words**
- [ ] **Metric to Watch: 1 line**
- [ ] **References: 1-4 lines**
- [ ] **CTA: 1 line**

### 3. FAILSAFE Components ✅
- [ ] **F - Failure:** Exact module/line specified
- [ ] **A - Assumptions:** Violated invariant stated
- [ ] **I - Inputs:** Trigger data/request identified
- [ ] **L - Loops:** Cascades documented
- [ ] **S - Safeguards:** Missing controls listed
- [ ] **E - Experiments:** Test confirmation described

---

## Email Client Testing Matrix

### Desktop Clients

#### Gmail Web
- [ ] Header renders correctly
- [ ] FAILSAFE cards display with proper spacing
- [ ] Impact stats bar shows 4 columns
- [ ] Fix steps numbered correctly
- [ ] CTA button clickable
- [ ] No clipping warning

#### Outlook 2016/2019
- [ ] Tables render without gaps
- [ ] Background colors display
- [ ] Font fallbacks working
- [ ] MSO conditionals functioning
- [ ] No broken layouts
- [ ] Buttons clickable (VML fallback)

#### Outlook 365
- [ ] Similar to Outlook 2016 checks
- [ ] Web version compatibility
- [ ] Dark mode doesn't break design

#### Apple Mail (macOS)
- [ ] Retina images display correctly
- [ ] Links trackable
- [ ] Typography consistent
- [ ] No rendering artifacts

#### Thunderbird
- [ ] Basic HTML structure intact
- [ ] Links functional
- [ ] Images load with alt text

### Mobile Clients

#### Gmail App (iOS/Android)
- [ ] Single column on narrow screens
- [ ] Text readable without zooming
- [ ] Buttons tap-friendly (44x44px minimum)
- [ ] Images scale properly
- [ ] No horizontal scroll

#### Apple Mail (iOS)
- [ ] Auto-scaling disabled
- [ ] Font sizes appropriate
- [ ] Links tappable
- [ ] Dark mode compatible

#### Outlook Mobile
- [ ] Tables stack properly
- [ ] Content readable
- [ ] CTAs accessible

---

## Common Issues & Solutions

### Issue: Gmail Clipping
**Symptom:** "[Message clipped] View entire message" link appears
**Solution:**
- Reduce HTML to < 102KB
- Remove unnecessary whitespace
- Consolidate inline styles

### Issue: Outlook Gaps
**Symptom:** White lines between table cells
**Solution:**
```html
<table cellpadding="0" cellspacing="0" border="0">
<!-- Add style="border-collapse: collapse;" -->
```

### Issue: Mobile Scaling
**Symptom:** Content too small or requires horizontal scroll
**Solution:**
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<!-- Use max-width: 600px; width: 100%; -->
```

### Issue: Dark Mode Problems
**Symptom:** White text on white background or invisible elements
**Solution:**
- Use transparent PNGs for logos
- Test with both light/dark modes
- Add dark mode meta tags:
```html
<meta name="color-scheme" content="light dark">
<meta name="supported-color-schemes" content="light dark">
```

### Issue: Images Blocked
**Symptom:** Broken image icons, missing visuals
**Solution:**
- Always include descriptive alt text
- Use background colors as fallbacks
- Keep critical info in HTML text

---

## Beehiiv-Specific Checks

### Platform Integration
- [ ] **Merge tags replaced** with Beehiiv variables
- [ ] **Tracking pixels** not duplicated
- [ ] **Unsubscribe link** properly inserted
- [ ] **Custom fields** mapped correctly

### Analytics Setup
- [ ] **UTM parameters** on all links
- [ ] **Click tracking** enabled
- [ ] **Open tracking** pixel present
- [ ] **Conversion goals** configured

### Beehiiv Variables
Replace these in your template:
```
[subscriber_name] → {{ subscriber.first_name }}
[email] → {{ subscriber.email }}
[unsubscribe] → {{ unsubscribe_url }}
[web_view] → {{ web_url }}
[issue_number] → Custom field
```

---

## Performance Benchmarks

### Target Metrics
- **Delivery Rate:** > 98%
- **Open Rate:** > 40%
- **Click Rate:** > 5%
- **Render Time:** < 3 seconds
- **Mobile Open Rate:** > 60%

### Size Targets
- **HTML:** < 90KB (recommended)
- **Images Total:** < 200KB
- **First Image:** < 50KB
- **Load Time:** < 3 seconds on 3G

---

## Final Pre-Send Checklist

### Content Review
- [ ] Spelling and grammar checked
- [ ] Links tested and working
- [ ] Asset download verified
- [ ] Metric formula accurate
- [ ] References cited correctly

### Technical Review
- [ ] HTML validated (no errors)
- [ ] Size under limits
- [ ] Mobile responsive
- [ ] Dark mode tested
- [ ] Images optimized

### Beehiiv Setup
- [ ] Subject line A/B variants ready
- [ ] Send time scheduled
- [ ] Segment selected
- [ ] Preview sent to team
- [ ] Final approval received

---

## Testing Tools

### Online Tools
- **Litmus:** Full email client preview
- **Email on Acid:** Cross-client testing
- **Mail Tester:** Spam score check
- **PutsMail:** Send test emails

### Browser Extensions
- **Mailtrack:** Open tracking test
- **Gmail HTML Inspector:** View actual rendered HTML

### Command Line
```bash
# Check HTML validity
curl -H "Content-Type: text/html" --data-binary @micro-autopsy-beehiiv.html https://validator.w3.org/nu/?out=json

# Measure size precisely
wc -c < micro-autopsy-beehiiv.html
```

---

## Post-Send Monitoring

### Hour 1
- [ ] Delivery rate normal
- [ ] No bounce spike
- [ ] Open rate tracking

### Hour 4
- [ ] Open rate on target
- [ ] Click tracking working
- [ ] No spam complaints

### Day 1
- [ ] Engagement metrics review
- [ ] Asset downloads counted
- [ ] Reply monitoring
- [ ] Feedback collected

### Week 1
- [ ] Full performance analysis
- [ ] A/B test results
- [ ] Optimization notes
- [ ] Template improvements logged

---

## Emergency Procedures

### If Email Fails to Send
1. Check Beehiiv status page
2. Verify HTML size < 102KB
3. Test with smaller segment
4. Contact Beehiiv support

### If Rendering Breaks
1. Deploy simplified version
2. Remove problematic components
3. Use text-only fallback
4. Schedule resend

### If Metrics Drop
1. Check spam folder placement
2. Review subject line
3. Analyze click heatmap
4. Survey subscribers

---

## Version History
- **v1.0** - Initial Beehiiv template
- **v1.1** - FAILSAFE framework integration
- **v1.2** - Mobile optimizations
- **v1.3** - Size reduction improvements

---

*Last Updated: September 2025*
*The Fix Loop - Ship Reliable Systems • Learn From Failure*