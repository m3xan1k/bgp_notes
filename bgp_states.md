## BGP states

- **Idle: No peering** — router is looking for neighbor
- **Idle(admin)** — means that the neighbor relationship is administratively down
- **Connect** — TCP handshake completed
- **OpenSent or Active** — an open message ws sent to try to establish the peering
- **OpenConfirm** — router has received a reply to the open message
- **Established** — routers have a BGP peering session. This is the desire state
    
---


