James Wilson
Personal site. One HTML file, no build step, no framework, nothing to install. The only thing it fetches is Google Fonts.

/ — the current site. A chat interface where the questions are already written and every answer is something I wrote by hand. There is no model behind it; the typing is fake.

/mac/ — the previous one. A working Macintosh System 7 desktop, with windows, a menu bar and a trash folder. Still there because I like it.

Live: https://jameswilsonlondon.github.io/about-me/

The idea
The site opens on a chat home screen. Every question is already written, so you just keep pressing send. Questions are asked in the second person and every answer is in the first person, so it reads as a conversation with me rather than an About page somebody else wrote about me.

There is an audience picker on the home screen, because two very different people land here:

Picker	Sidebar shows
Just having a look	Start here, why this site exists, the path, Ethiq, the CV, the podcast, the builds
I am hiring engineers	How I run a search, why me, the market, clients, what I am not good at
I am an engineer	What happens if I contact you, what is out there, am I underpaid, what next
The 19 threads are built from things already public: my LinkedIn work history, my GitHub repos, the podcast feed, the Ethiq site and my live roles page.

Editing it
Everything worth changing lives in the T array near the top of the <script> block. One object per conversation:

{
  id:'start',                        // used in the ?t= deep link
  title:'Start here',                // sidebar label
  aud:['nosy','founder','engineer'], // which audiences see it
  q:'Who are you and what do you do?',  // the prefilled question
  tool:{n:'sources.read', d:'...'},     // optional tool-call chip
  b:[ ...blocks... ],                // the answer
  next:['why-site','path','ethiq']   // follow-up chips
}
Block types for b:

{t:'p', c:'...', lead:true} paragraph (lead makes it the big serif opener)
{t:'h', c:'...'} subheading
{t:'ul', c:['...','...']} bullets
{t:'q', c:'...'} pull quote
{t:'kv', c:[['Label','Value'], ...]} two column table
{t:'links', c:[{l:'Label', h:'https://...'}]} link pills
{t:'art', title, sub, b:[...blocks]} expandable card
Audience labels and greetings are in AUD. The joke model versions are in MODELS.

URL parameters
?mode=playback autoplays three threads. Good for a screen recording.
?t=cv deep links straight into a thread.
?as=founder opens with that audience preselected.
The logo
markSVG() draws six rounded capsules rotated in 30 degree steps, which reads as a twelve spoke burst. Two are trimmed slightly so it is not perfectly uniform. Colour is the --mark variable in :root. Everything else on the page stays sage, so the clay is only ever the mark.

Notes
Theme follows the system on first visit, then remembers the toggle.
Works on a phone. The sidebar becomes a drawer.
Clicking anywhere or hitting Escape skips the typing animation.
The name top left goes back to the home screen, same as New chat.
Typing something I have not written gives a fallback pointing at my email.
serve.js is only for local preview (node serve.js, then localhost:8899). GitHub Pages does not need it.
