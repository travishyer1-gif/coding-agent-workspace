# WISP Domain Context

**Company:** Advantage WISP (Advantage Telecom)  
**Service Area:** Ventura County, California  
**Business:** Fixed Wireless Internet Service Provider

---

## Network Infrastructure

### Technology Stack
- **Radios:** Ubiquiti airFiber, LTU, LiteBeam
- **Management:** UISP (Ubiquiti ISP)
- **Billing:** VISP
- **Frequencies:** 5 GHz, 6 GHz (CBRS)

### Network Stats
- ~1,000 devices (86 APs, 464 CPEs)
- 13 tower sites across Ventura County
- Main coverage: Ventura, Oxnard, Camarillo, Santa Paula, Fillmore, Somis

### Key Tower Sites
- Willis Peak
- Butler Tower
- Peterson
- Kimball
- And 9 others

---

## Data Access

### Available APIs
1. **UISP API**
   - Endpoint: `https://uisp.advantagewisp.com/nms/api/v2.1`
   - Auth: Read-only API key in `~/.secrets/uisp-api-key`
   - Data: Device status, signals, alerts, network topology

2. **VISP API** 
   - GraphQL endpoint
   - JWT auth (expires periodically)
   - Data: Customer billing, packages, accounts

3. **Outlook (Microsoft Graph)**
   - OAuth2 tokens
   - Access: Work email, calendar, contacts
   - Account: thyer@advantagewisp.com

### Local Databases
1. **customer-lookup.db** (`~/clawd/data/work/customer-lookup.db`)
   - SQLite, 1,000 devices indexed
   - Customers, devices, APs, sites
   - Fast lookup by name/IP/MAC/AP

2. **coworkers.db** (`~/clawd/data/work/coworkers.db`)
   - Company contacts and roles

3. **Customer Master Database** (Excel)
   - `~/clawd/data/work/Customer_Master_Database_v3.xlsx`
   - Network master sheet, billing info, AP/CPE radios

---

## Common Use Cases

### Customer Service
- Look up customer by name/IP/MAC
- Check signal quality and connection status
- Find AP assignments
- Pull billing information

### Network Operations
- Monitor AP health and load
- Identify poor signal quality
- Track outages and downtime
- Plan tower upgrades

### Business Intelligence
- Revenue per tower/AP
- Customer churn risk scoring
- Network health metrics
- Installation pipeline

---

## Existing Tools

Located in `~/clawd/scripts/`:

### Customer Data
- `customer-lookup.py` - Fast unified search
- `visp.py` - Billing system queries
- `customer-db-sync.py` - Database refresh

### Network
- `uisp_lookup.py` - Device lookups
- `wisp-network-health.py` - Health scoring
- `wisp-churn-score.py` - Customer health
- `wisp-revenue-analysis.py` - Revenue metrics

### Communications
- `outlook.py` - Email/calendar integration
- `coworkers.py` - Contact lookup

### Workflow
- `trello.py` - Project management
- `calendar-request-procedure.md` - Field work scheduling

---

## Field Operations

### Team
- **Patrick** - Field technician (can schedule directly)
- **Paul** - Field technician (check with Tiffany first)
- **Peter** - Owner
- **Christophe** - Office/Network Operations Manager
- **Tiffany** - Scheduling coordinator
- **Travis** - Director of Operations

### Scheduling Rules
- Morning slot: 8 AM - 12 PM (difficult/longer jobs)
- Afternoon slot: 1 PM - 5 PM (easier/shorter jobs)
- Priority: Repairs > Installs > Site Surveys

---

## Development Guidelines

### When Building WISP Tools

1. **Security First**
   - All work credentials in `~/.secrets/` (600 perms)
   - All work data in `~/clawd/data/work/` (700 perms)
   - Never log sensitive data
   - Gitignore both directories

2. **Data Access Pattern**
   - Use customer-lookup.db for speed
   - Fall back to APIs for fresh data
   - Cache when appropriate
   - Respect rate limits

3. **Output Formats**
   - Support `--json` flag for scriptability
   - Human-readable default output
   - Telegram-friendly formatting (no markdown tables)

4. **Error Handling**
   - Graceful degradation
   - Helpful error messages
   - Log to stderr, data to stdout

5. **Integration Points**
   - Outlook for scheduling
   - Trello for project tracking
   - UISP for network state
   - VISP for billing

---

## Project Ideas

### High Priority
- Customer self-service portal
- Real-time network monitoring dashboard
- Automated outage detection and notification
- Install/repair scheduling automation

### Medium Priority
- Tower site ROI calculator
- Customer churn prediction model
- Automated invoice generation improvements
- Mobile field tech app

### Nice to Have
- Coverage map visualization
- Weather correlation analysis
- Competitor monitoring automation
- Customer referral tracking

---

## Notes

- Company operates M-F, 8 AM - 5 PM PT
- Field work requires 2 techs for tower climbs
- Base work (Pt Mugu Naval Base) is a recurring commitment
- Equipment typically ships from Ubiquiti (lead times vary)

---

*Last Updated: 2026-02-06*
