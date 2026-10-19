SignBridge: Universal Two-Way Counter Kiosk
Helping deaf, non-verbal, elderly and low-literacy people be understood at service counters, with no sign language and no typing needed.
Live demo · Demo video · Presentation  <!-- replace # with your links -->
---
The problem
Deaf, speech-impaired and elderly people face real barriers at pharmacies, hospitals, banks and railway counters. Most sign-language translators assume the user knows formal sign language, but many do not. Typing full sentences is slow or impossible for people with low literacy or motor difficulties. The result is pointing, miming, hurried notes, long queues and risky misunderstandings, especially about medicines.
Census 2011 recorded about 5.07 million people in India with hearing disability and about 2 million with speech disability.
Our solution
SignBridge is a countertop kiosk (tablet or laptop) that works in both directions.
Customer to staff: the customer taps picture cards, and the kiosk speaks a clear sentence to the staff.
Staff to customer: staff reply by voice or typing, and the screen shows large text plus simple pictograms.
Key features
Feature	What it does
Picture tap-board	Symptoms, duration, previous medicines, age, and a 1 to 10 severity scale, all by tapping icons and faces
Own-words box	Optional typed description, read out to the pharmacist along with the picture choices
Spoken summary	The kiosk reads the full message aloud, only when the customer presses the button
Staff reply	Pharmacist types or speaks, and the display shows the medicine, how often, number of days, doctor type to meet and cost
Finger counting	Webcam hand tracking turns 1 to 5 fingers into a number (age or days) in `signbridge_kiosk.html`
Safe by design	Sentences come from fixed templates, so nothing is invented. The pharmacist confirms everything
Private	Hand tracking runs on the device, and no video is stored or uploaded
Why it is different
Most projects assume every deaf user knows sign language. SignBridge combines pictures, natural gestures and a two-way pictogram reply, so it works for deaf, non-verbal, elderly, low-literacy and temporarily speech-impaired users.
How it works
```
Customer: tap icons / show fingers / type note
        |
        v
Structured data (symptom, duration, age, severity, past medicines)
        |
        v
Template sentence  -->  spoken aloud to pharmacist
        |
Pharmacist replies (voice or text)
        |
        v
Rule parser (medicine, frequency, days, doctor, cost)
        |
        v
Large text + pictograms for the customer
```
Tech stack
Frontend: HTML, CSS, JavaScript (no build step)
Gesture tracking: MediaPipe Hand Landmarker (on-device)
Voice output and input: Web Speech API (Chrome)
Intent and reply logic: rule-based templates and a fixed pictogram and medicine list
Hardware: laptop or tablet with webcam, microphone and speaker
Run it locally
Download or clone this repository.
Open `index.html` in Google Chrome (the full pharmacy kiosk).
For the finger-counting demo, open `signbridge_kiosk.html`, press Start camera and allow access. It needs internet on first run to load the hand-tracking model.
If the browser blocks the camera or microphone, run `python -m http.server` in this folder and open `http://localhost:8000`.
Live demo script
Mode 1, customer to staff: tap [Stomach pain] + [Child], choose Age, show 3 fingers. The kiosk previews, then speaks: "I need medicine for a 3-year-old child with stomach pain."
Mode 2, staff reply: the pharmacist says "Take paracetamol twice a day after food for 3 days. See a general physician if the fever continues. Cost 120 rupees." The screen shows the medicine, sun and moon icons, a plate for after food, 3 days, the doctor type and the cost.
Project structure
```
signbridge-kiosk/
├── index.html            # Full pharmacy kiosk page
├── style.css             # Large, simple, light and dark styling
├── data.js               # Icons, medicine list, sample prices, doctor types (edit here)
├── app.js                # Input, spoken summary, reply parsing
├── signbridge_kiosk.html # Standalone demo with webcam finger counting
└── README.md
```
Safety and limits
Medicine prices are sample values for demo only.
The doctor type is shown only if the pharmacist says it.
The kiosk communicates. It does not diagnose or prescribe, and the pharmacist always confirms medicines, doses and costs.
Voice features need Chrome and an internet connection. Language is currently English (en-IN).
Roadmap
[x] Picture tap-board with duration, medicines, age and severity
[x] Spoken summary and staff reply with pictograms, days, doctor type and cost
[x] Webcam finger counting (standalone demo)
[ ] Merge finger counting into the full kiosk
[ ] Thumbs up/down, head nod/shake, and body-part pointing diagram
[ ] Tamil and Hindi voices and text
[ ] Icon sets for hospitals, banks and railway counters
[ ] Pilot at a real pharmacy, measuring time per interaction and error rate
References
Census of India 2011, disability data
Rights of Persons with Disabilities Act, 2016
MediaPipe Hand Landmarker
Web Speech API (MDN)
