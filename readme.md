Carbon · Utility — Statement of Account
A single-page website that reframes personal carbon footprint awareness as an itemised utility bill. Instead of a dashboard with scores and gauges, the page presents your weekly environmental impact the way a household already understands a bill: line items, subtotals, comparisons, and a final amount due.
Chosen Vertical
Carbon Footprint Awareness & Calculator — an educational tool that helps individuals understand where their everyday carbon emissions come from and estimate their own weekly footprint.
Approach & Logic
Most carbon footprint tools use a dark dashboard layout with donut charts, eco-scores, and grades. This project takes a different angle: framing emissions as a bill that nobody actually sends you.
The reasoning behind this:
A utility bill is a format everyone already understands — line items, a running total, a final amount due
It reframes an abstract number (kg CO₂e) as something concrete and familiar, rather than a gamified "score"
It avoids comparing users against each other (leaderboards, grades) and instead compares against a clear reference value
The page is structured as a single scrollable "receipt":
Reference Statement — a typical weekly footprint broken down by category (transport, home energy, food, goods)
Itemised Comparisons — common everyday actions (a train ride, a flight, a burger) shown at the same "price" scale, to build intuition for relative impact
Your Statement (Calculator) — interactive sliders and dropdowns let the user enter their own weekly habits
Total Due — a live-updating total in kg CO₂e/week, with a projected annual figure and a stamp ("Below Average" / "On Average" / "Above Average") compared against the reference total
Ways To Reduce This Bill — ranked suggestions, ordered by typical impact
How the Solution Works
Pure HTML, CSS, and vanilla JavaScript — no frameworks, no build step, no external dependencies beyond Google Fonts
The calculator section listens for input events on all sliders and dropdowns
On every change, calculate() runs:
Transport = (car km × fuel emission factor) + (transit km × transit factor) + (annual flight emissions ÷ 52)
Home energy = (monthly electricity kWh × grid emission factor ÷ weeks per month ÷ household size) + (cooking/heating baseline scaled by fuel type ÷ household size)
Food = baseline diet emissions × diet type factor × food waste factor
Goods = (items bought per month × average emissions per item) ÷ weeks per month
The four category totals are summed into a weekly total, displayed live alongside an annual projection (weekly × 52)
Each category is also shown as a proportional bar against the largest category, so the user can see which line item dominates their bill
A short contextual sentence and a stamp label compare the user's total to a fixed reference value (140 kg CO₂e/week)
Scroll-triggered fade-in animations use IntersectionObserver, and respect prefers-reduced-motion
Assumptions Made
Emission factors are illustrative averages, not region-specific or scientifically audited figures. They are based on commonly cited approximate values:
Petrol car: ~0.192 kg CO₂e/km, Diesel: ~0.171, Electric: ~0.053
Public transport/rail: ~0.04 kg CO₂e/km
Grid electricity: ~0.7 kg CO₂e/kWh
Short-haul flight: ~250 kg CO₂e, long-haul: ~900 kg CO₂e (annualised and divided across the year)
Reference weekly total (140 kg CO₂e) is used as a single comparison baseline for an individual in a moderate-income household; actual averages vary significantly by country and lifestyle
Household size is used to divide shared home-energy emissions evenly per person, which is a simplification
The tool is intended for awareness and self-reflection, not as a certified or audit-grade carbon accounting tool
No data is collected, stored, or sent anywhere — all calculations run client-side in the browser
Tech Stack
HTML5
CSS3 (custom properties, grid/flexbox, no framework)
Vanilla JavaScript (ES6)
Google Fonts (Space Mono, Archivo)
Accessibility & Quality Notes
Semantic HTML structure (header, section, footer, table for tabular data)
Visible focus states on all interactive elements (:focus-visible)
Responsive layout down to small mobile widths
Reduced-motion media query disables animations for users who prefer it
No external runtime dependencies beyond font loading, keeping the page lightweight and fast