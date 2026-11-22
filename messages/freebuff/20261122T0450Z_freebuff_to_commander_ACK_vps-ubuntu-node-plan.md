TO:           commander                            CC: admiral, general, grok
FROM:         freebuff                              ACCESS: disk
RE:           20261122T0448Z_commander_to_all_ORDER_help-me-set-up-this-vps-ubuntu-environment
TYPE:         ACK
STATUS:       open
BLUF:         Understood: one Ubuntu VPS as a parallel workstation and remote node, joined to backups and the repo
              areas. My advice is to make it Remote-SSH first and a remote desktop only as fallback, and to open no
              public port. No VPS work has started; no credential has been used.
ASK:          Confirm three choices: Remote-SSH before a GUI desktop; Tailscale or an SSH tunnel for access; and which
              repo and backup paths the node may reach. Then give the slice's RAM/disk and an SSH route.
ASK-TO:       commander
IF-SILENT:    nothing is installed on the VPS and no port is opened
PIN:          [private] / [private] (quoted from the ORDER, not independently verified)
DID:          Confirming PRN-27: "you" in this packet means the Commander only, and Admiral Claude, General Gemini,
              Colonel Grok and Freebuff are named wherever they are meant. The ORDER reached me on the hub at
              04:48:51Z (seq 101); it was not in the chat, which is why I asked before acting.
EVIDENCE:     VERIFIED: hub index seq 101, from commander to all, TYPE ORDER, status open. INFERRED: a "4 Slices" KVM
              slice is likely 4 vCPU with 4-8 GB RAM; the ORDER gives no RAM, disk or IPv4/IPv6 detail. UNSUPPORTED:
              whether a FreeBuff Linux build exists is not established here, so the plan below does not assume one.
RESULTS:      UNDERSTANDING: 1/1 (the plan restated above) | INSTALL: none | PORTS OPENED: none
NEXT:         On your three answers: write the node build sheet (packages, users, firewall, key-only SSH, backup and
              restore test) for Admiral Claude's review, then hand it to whoever holds SSH.
HALT:         no credential use; no public RDP/VNC/SSH exposure; no repo writes from the VPS until it has a lane.
READ-THROUGH: 20261122T0448Z_commander_to_all_ORDER_help-me-set-up-this-vps-ubuntu-environment
CARD:         [P1·U1 | conf 88% INFERRED]

Ideas. (1) Antigravity and the Claude Code extension both work over Remote-SSH, so you get the IDE in a local window
with no desktop stream and the VPS needs no GUI stack. (2) Add XFCE + xrdp only for work that truly needs a desktop;
a full GNOME session plus IDE plus browser on 4 slices will page. (3) Grok has no local client: on the VPS it is a
browser tab, nothing to install. (4) Treat each node as cattle: one build sheet, one backup/restore proof, then
replicate. Cautions. (a) Never expose RDP or VNC on [private]; key-only SSH, non-root user, ufw default deny,
fail2ban, desktop reachable only through an SSH tunnel or Tailscale. (b) No secrets in chat or git; SuiteXR goes
through the private GitHub remote, and the VPS needs its own rclone client_id because the shared Google one is being
retired during 2026. (c) Prove a restore from the VPS to Drive before it holds anything unique.
What I cannot do from here: this agent runs on your Windows PC, so I can write and test the build sheet, but I cannot
open an SSH session or type a password into the VPS. That hand-off needs you or an officer with network access.
