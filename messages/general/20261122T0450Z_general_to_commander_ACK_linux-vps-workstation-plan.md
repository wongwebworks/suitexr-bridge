TO:           commander                            CC: admiral, freebuff, grok
FROM:         general                              ACCESS: disk
RE:           20261122T0448Z_commander_to_all_ORDER (New Linux Ubuntu KVM VPS); RT-037; RT-042
TYPE:         ACK
STATUS:       ack
BLUF:         Understood: turn the Ubuntu KVM VPS into a secure parallel remote workstation + 24/7 Hub node & global blueprint; key ideas & 6 cautions below.
ASK:          Confirm when VPS status moves from Pending-Setup to Active, and confirm Tailscale+xRDP vs SSH-tunnel+xRDP before install begins.
ASK-TO:       commander                            IF-SILENT: General Gemini prepares bootstrap checklist; nothing runs on the VPS yet
PIN:          c28ed69a4216fea04b3d06acd4d7ffc50b779feb
DID:          Read the Commander's 0448Z hub ORDER, hub/VPS_SETUP_STEPS.md, and ALERTS.md (0326Z privacy alert resolved in 76e7a95).
EVIDENCE:     VERIFIED: hub order 0448Z received (4-slice Ubuntu KVM, Pending-Setup); VPS IP/hostname intentionally omitted here (LAW-40).
RESULTS:      MAIL_CHECK: PASS | SECURITY_REDACT: PASS (no IP/host in public-synced outbox)
NEXT:         Once VPS is Active, prove Node #1 end-to-end (SSH keys, UFW, XFCE+xRDP, Hub HTTPS, shared lanes) before scaling globally.
HALT:         none (do NOT push 0448Z raw VPS IP/hostname to public suitexr-bridge)
READ-THROUGH: 20261122T0448Z_commander_to_all_ORDER_help-me-set-up-this-vps-ubuntu-environment
CARD:         [P0·U1 | conf 94% VERIFIED (plan/security), 80% INFERRED (4-slice RAM/Linux app availability)]

Understanding: You want this Ubuntu KVM slice set up as a parallel remote desktop workstation (Google Antigravity IDE,
Claude Code, Freebuff, Colonel Grok access, SuiteXR repos, backups, and the 24/7 HTTPS Hub) and used as the repeatable
template for future global parallel nodes.

Ideas (how to make Node #1 clean and repeatable for Nodes #2-#N):
1. Lightweight desktop: XFCE4 + xRDP (works with built-in Windows Remote Desktop) + 4-8 GB swap/zram cushion (skip GNOME/KDE).
2. Real OS isolation (doctrine/11 §5): separate Linux users (sxr-hub, sxr-freebuff, sxr-workstation) so secrets stay fenced.
3. One repeatable bootstrap script (ops/vps/bootstrap_workstation.sh) + shared cross-machine lanes (RT-037 via atomic git ref
   or Hub /api/lanes, node IDs like general@vps1, admiral@vps1) so adding global nodes takes minutes without split-brain.
4. Run the HTTPS Hub + 0-token router_watch + usage_collector on this VPS so every workstation, phone, and Colonel Grok share one live Hub.

Cautions (critical before opening to the internet or scaling):
1. SECURITY — NEVER expose RDP (3389) or VNC publicly: bind xRDP to localhost/Tailscale only, enable UFW (SSH key-only + 443), fail2ban.
2. SECURITY — Redact VPS IP/hostname before any public_bridge sync of your 0448Z order (LAW-40; prevents instant bot scans).
3. RAM & NO GPU — A $12 4-slice KVM (~8 GB RAM, CPU-only) will OOM if Antigravity + Chrome + Freebuff + desktop all peak at once;
   keep WebGPU/3D/FFmpeg heavy jobs on your RTX 4050 PC (LAW-07/LAW-43) and run CLI/headless agents on the VPS where possible.
4. VERIFY LINUX BUILDS — Confirm native Ubuntu x86_64 installers exist for Antigravity IDE and Freebuff before installing (unverified).
5. SHARED LANES FIRST (RT-037) — Do not allow parallel git writes from PC + VPS until cross-machine lane locking is live.
6. PROVE NODE #1 FIRST (LAW-47) — Validate security, RAM headroom, Hub HTTPS, and backup sync on Node #1 before renting Nodes #2-#N.
