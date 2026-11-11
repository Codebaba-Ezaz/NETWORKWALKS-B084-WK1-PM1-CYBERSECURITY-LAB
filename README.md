<div align="center">

# SOC Wireshark Project

### Network Forensics Labs | Networkwalks 1-Month Training | Week 1

**Ezaz Ahmed**

<a href="https://www.linkedin.com/in/ezaz-ahmed-sayem/" target="_blank">
  <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
</a>
<a href="https://github.com/Codebaba-Ezaz" target="_blank">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
</a>

</div>

---

## 👋 About This Project

I did this project in **Week 1** of my **Networkwalks 1-month training**. The task was to act as a SOC analyst and investigate 6 browser-based Wireshark labs. Every lab comes with a packet capture and 10 tasks, so I worked through 60 tasks in total, from tracking down an attacker's IP to listening to a scam call.

I finished all 6 labs. This repo is my record of what I did and what I learned.

---

## 🧪 Labs I Completed

| Lab | Title | What I worked on | Status |
|:---:|-------|------------------|:------:|
| 3 | Identify the Attacker's IP | Finding the attacker's IP address in the traffic | ✅ |
| 4 | Follow TCP Stream 1 | Rebuilding a conversation and reading what was sent | ✅ |
| 5 | Follow TCP Stream, Part 2 | Following streams on a new capture to find hidden data | ✅ |
| 6 | HTTP Plain Text Credentials | Finding usernames and passwords sent in clear text | ✅ |
| 7 | Catch the Brute Force Attacker | Spotting repeated login attempts and the source behind them | ✅ |
| 8 | Catch the Call Scammer | Investigating the capture and replaying the VoIP call | ✅ |

---

## 🔍 Lab Walkthroughs

### 🎯 Lab 3: Identify the Attacker's IP

The scenario: a staff member reported unusual traffic to the company web server. I captured the packets and had to work out what kind of attack it was and who was behind it.

I filtered for SYN packets with `tcp.flags.syn == 1`. Most PCs only send one or two of these, but one host was sending a long run of them, one after another, to a different port each time (21, 25, 80, 110, 139, 3389, 5900 and more) from the same source port. That pattern is a port scan, and the host sending it was `192.168.10.66`, scanning `192.168.10.20`.

![Lab 3: Identify the Attacker's IP](images/lab3-identify-attacker-ip.png)

---

### 🔓 Labs 4, 5 and 6: Follow TCP Stream and clear-text credentials

In these labs I practiced rebuilding full conversations with **Follow → TCP Stream**, finding hidden data inside captures, and spotting usernames and passwords that were sent in clear text over HTTP. Seeing credentials appear as plain readable text in a stream really showed me why HTTP is risky and why HTTPS matters.

---

### 🔨 Lab 7: Catch the Brute Force Attacker

Here I looked for repeated login attempts in the capture and worked out which source was guessing passwords. A lot of failed attempts from one address in a short time is the main sign to look for.

---

### 📞 Lab 8: Catch the Call Scammer

The scenario: a phone call was made through the company VoIP system. I had to capture the traffic, find the call and play it back to learn what was said.

I filtered with `sip` and could see the whole call setup: an `INVITE` from `192.168.10.45` to `192.168.10.52`, then `100 Trying`, `180 Ringing`, `200 OK`, the `ACK`, and finally the `BYE` that ended the call. SIP sets up the call, and the audio itself travels over RTP, which is what I used to play it back.

![Lab 8: VoIP call replay](images/lab8-voip-call-replay.png)

---

## 🛠️ Skills I Practiced

- 🎯 Spotting an attacker by their traffic pattern
- 🔗 Rebuilding conversations with Follow TCP Stream
- 🕵️ Finding hidden data inside captures
- 🔑 Finding clear-text credentials in HTTP traffic
- 🔨 Detecting brute-force login attempts
- 📞 Analysing SIP and RTP traffic and replaying a VoIP call

## 🧰 Tools and Filters

- **Wireshark** (browser-based lab environment)
- Display filters such as `tcp.flags.syn == 1` and `sip`
- Follow → TCP Stream
- Telephony → VoIP Calls

---

## 💡 What I Learned

- A port scan stands out clearly in a capture: one host, many SYNs, many different ports.
- Anything sent over plain HTTP can be read by whoever captures it.
- Many failed logins from one source in a short time points to brute force.
- Packet captures can show who attacked, and also what was said and sent.

## ⚖️ Ethics

I only worked inside the provided labs. I will never capture or test traffic on a network I don't own or don't have written permission to test.

## 🙏 Thanks

Thanks to [Networkwalks](https://networkwalks.com/) for the labs and the training program. All labs are available at [networkwalks.com/wireshark](https://networkwalks.com/wireshark/).

---

<div align="center">

Made by **Ezaz Ahmed**

</div>
