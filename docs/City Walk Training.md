# City Walk Training

## Description

An author's personal service agent for direct interaction.

A flexible, dynamic, self-adjusting system focused on the user's interests during a private event. The application is centered around voice communication, with additional use of sound signals, tapping, vibration, Morse code, and Q-codes.

### Core Functions

1. **Recommendations:** Providing advice and tips during the event (e.g., where to go next).
2. **Escort/Guidance:** Instructing the user, leading along a route.
3. **Configuration:** Ability to adjust parameters, implement memory functionality (preferences/state).
4. **Communication Chains:** Integrated use of blockchain technologies (specific use case needs clarification).
5. **Communication:**
	- General chat (text, images, video) via the agent.
	- Optional peer-to-peer communication (voice to text, text to voice, `personal agent 2 personal agent`).
6. **Announcement of new technology, interaction protocol:**  
	**[[Personal Agent 2 Personal Agent]]** (`PAPA`)

### Access

Personal application, distributed by personal invitation only for friends within the private event.

>[!i] Access management is currently not considered. Planned to be implemented as simple database entries.

<div style="page-break-after: always;"></div>

## Event Concept

- **Format:** 12-hour event (10:00 - 22:00) in the form of a city walk-workout.
- **Organization Task:** Participants must be physically, mentally, and psychologically capable of completing the entire event. Load and relaxation must be properly distributed.
- **Participants:** 50-100 people.
- **Groups:** 1 to 4 people. Groups may temporarily merge or intersect.
- **Main rule:** Avoid drawing unnecessary attention, behave like ordinary citizens/tourists.
- **Interaction:**
	- Moving around the city is the basic activity.
	- Group meetings at various points (parks, cafes, embankments).
	- Interaction points — activities that do not require explicit task completion or puzzle-solving in the traditional sense. Focus on exploring reality (physical, informational).
	- Workshops (optional, held by participants voluntarily). Topics determined by hosts.
	- Information exchange between groups upon meetings.
	- Possible performances or flash mobs, adapted to avoid drawing attention.
- **Psychological Aspects:**
	- Importance of participants' psychological comfort, agent empathy, interactivity, and personalization.
	- Goal — creating a symbiosis between participant and agent, where the agent is helpful, unobtrusive, and evokes positive emotions.
- **Routes:**
	- The system recommends a route and the next location point.
	- Participants can alter the route as they wish.
	- A database of places is used, classified (rest, interaction, systemic place, pleasant/unpleasant, etc.) with descriptions.
	- Maps are provided via links to external services (OpenStreetMap, Google Maps).

<div style="page-break-after: always;"></div>

## Technical Implementation (Agent)

### Mobile Application

- Stable internet connection required to use cloud services.
- Permissions needed for microphone and internet access, plus hardware (microphone, speaker).

### Interfaces

>[!i] Primary focus on voice interaction, supplemented with sounds, vibration, tapping, Morse code, and Q-codes.

- **Minimalist Interface:** Primary focus on voice interaction. Possible text chat.
- **Voice Communication:**
	- **voice2voice:**
		- Voice to text for command/message input (Cloud Speech-to-Text).
		- Text to voice for information/message output (Cloud Text-to-Speech).
	- Native Android APIs (SpeechRecognizer and TextToSpeech) are less accurate and limited, suitable only for offline mode.
	- Cloud architecture recommended (e.g., Google Cloud Dialogflow, STT, TTS) for high quality and scalability.
- **Additional Signals:**
	- **audio (mix):**
		- music
		- sounds / effects
		- morse
	- Vibration
	- Tapping
- **Input:**
	- **sensors / detect triggers:**
		- direction
		- position
		- tap
		- move
		- gestures
		- walk
	- **full audio:**
		- FFT

<div style="page-break-after: always;"></div>

- **Views and Services:**
	- text view
	- external maps
- **Architecture:**
	- Use of a backend proxy to manage API keys and cloud service calls, ensuring security and flexibility.
	- Android microphone background access limitations handled via Foreground Service.

### Use of Morse Code

Intended to facilitate and speed up communication and signal perception. Morse code is more of a desired or expected functionality. Such signals can be transmitted parallel to other information (e.g., dialogue or navigation). Commonly accepted standards are used.  
Morse code is excellent for transmitting short messages or hints, and Q-codes for more complex information like coordinates or instructions.

- Use of sound signals, vibration, Morse code (especially Q-codes for standard messages) to transmit information in parallel with voice.
- **QTC:** "I have a message for you."
- **QRU:** "I have nothing for you."

### Agent Triggers (Prompt Examples):

1. **Sending to general chat:** "When the user says something clearly indicating a desire to share information with the group in the general chat (e.g., 'Send to general chat...', 'Pass to everyone in chat...', 'Write to general chat...', 'Inform the group...'), offer to send the message to chat and confirm if they wish to do so."
2. **Request for recommendation/next step:** "When the user asks for a recommendation or advice on what to do next (e.g., says: 'Where should I go now?', 'What's next?', 'What to do after this?'), suggest the next step or location from the database."
3. **Request for alternatives/list:** "If the user disagrees with a recommendation, asks about other options ('Are there other options?', 'I want to visit another place') or requests a list ('Please read the whole list'), provide alternative options from the database or the first 5 relevant places."

### Location Database

A list of places with classifications, descriptions, and selection conditions. Available to the agent for generating recommendations.

### Blockchain ("Communication Chains")

- Specific application and value need clarification.
- **Blockchain Functions:**
	- Demonstrative.
	- As an internal interaction system.
- **Implementation:**
	- Private key generation locally on the user’s device using their input entropy.
	- Define the list of supported networks and the base network (polygon, binance, solana).
	- Credit initial balance for transactions.
	- Operating contracts (transfer/distribution).
	- \~ setting triggers.

## Installations and Recommendations for Event Passage

### Main Task — Complete the Whole Event

As a training, meaning to be physically and mentally capable of completing the entire event from 10 AM to 10 PM (12 hours). It's a lot. Therefore, load and relaxation must be distributed.

### Load Distribution

The agent should help distribute load and relaxation throughout the 12 hours, including context switching to reduce fatigue.

>[!i] Time is set by intervals.  
> $\Delta T_{\text{activity}} \in [2~\text{h}, 3~\text{h}]$  
> $\Delta T_{\text{recreation}} \in [25~\text{m}, 45~\text{m}]$
>
> Which means:
>
> * Recommend a half-hour recreation every 2–3 hours.
> * Recommend a short break every 25–45 minutes.

<div style="page-break-after: always;"></div>

### Recommendation System

- **Modules:** Positioning.
- **Inputs:**
	- geolocation, specified location, completed route
	- wishes (regarding the route)
	- instructions

### Operational follow-up system
Real-Time Guidance System

- Provides real-time high-priority instructions.

### "Flexibility, Dynamism, Self-Adjustment":

- **Manifestation:** The system will adapt to user behavior and scenario changes during the event.
	>[!i] Yes, using a memory mechanism the system will adjust its parameters in real time based on user wishes and dynamic event context.

- **Mechanism:** Context switching and load management for participants through analyzing their actions and preferences (open question for further development).

### Configuration/Memory:

- **Which parameters can the user configure?**
- **What exactly should the system "remember"?**
	>[!info]
	> route
	>- meetings, visits, operations
	>- marked information and dialogues
	>- parameter changes

<div style="page-break-after: always;"></div>

## Open Questions and Proposals for Discussion

To move toward the implementation plan, I suggest delving into details and clarifying several points:

1. **Event Context:**
	- What is the nature of the private event? (e.g., quest, interactive game, performance, educational seminar?) Understanding the context will help specify the recommendation and escort functions.
	- What *specific* tasks or actions will the user perform using the agent during the event?
2. **Function Detail:**
	- **Recommendations/Escort:** What exactly will the agent advise/instruct? Based on what (event scenario, user actions, their preferences)?
	>[!info]
	>- [[#Recommendation System]]
	>- [[#Real-Time Escort System]]
	- **Configuration/Memory:** Detailed in [[#Configuration/Memory:]].
	- **Blockchain:** Detailed in [[#Blockchain ("Communication Chains")]].
3. **Non-Standard Interfaces:**
	- In which scenarios are Morse, tapping, Q-codes planned to be used? Are they a primary way of interaction in some situations or supplementary? Detailed in [[#Use of Morse Code]].
4. **Clarification of "Interaction Points":** What exactly will the activities/explorations of reality involve?
5. **Mechanism of agent "self-adjustment":** How will it adapt?
6. **Creation of the location database:** Need a list of specific places with their classifications.
7. **Workshop detailing:** How will participants announce their workshops? How will others learn about them?

**[Next Steps]**

I suggest starting by clarifying the **event context** and the **specific user tasks**. This will allow us to further develop the functions and understand which technologies (including blockchain and non-standard interfaces) are truly necessary and how best to implement them.

## Discussion Notes

- Using all possible signals: sound, vibration to transmit information (not just to attract attention).
- Groups of 1–4 people, possible intersections and temporary mergers. Possible meeting points.
- Avoid creating a sense of excessive community even during meetings.
- Avoid the term "tasks," use: "interaction points."
- Activity ideas (item exchange, flash mob) — remember but don't explicitly include yet.
- Free communication — basic value.
- Workshops. Provided for invited friends with author-led workshops.
- Activities should be hybrid (physical, creative, informational) ⚠️ not drawing attention.
- Teamwork and explicit tasks — not the focus.
	- Art objects/performances — adapt to avoid attention.
- Participants must *look* like city dwellers/tourists and not necessarily *feel* like them (separate topic).
- **Plan:**
	1. Collect and classify a list of places.
	2. Use this list by the AI agent for route recommendations.
- Map (external).
- Chat — via the agent, optionally P2P (voice→text→voice).
- Trigger for sending to general chat.
- Formulation of prompt triggers for the agent (general chat, recommendation request, alternatives request).
