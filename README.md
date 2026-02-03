Wede: Offline Resiliency SDK (Multi-Chain DePIN)
Status: v0.1 (Private Beta) License: Proprietary / Open Core
Overview
Wede is a middleware layer designed to provide Offline Resiliency for DePIN (Decentralized
Physical Infrastructure Networks). It ensures that edge devices (sensors, cameras, trackers) can
maintain state synchronization and local consensus even when IP connectivity degrades or fails
(e.g., during 5G/4G outages).
Architecture
Wede operates on a Dual-Layer &quot;Open Core&quot; Architecture:
1. The Integration Layer (Open SDK)
 Connectivity Monitoring: Real-time listeners for signal degradation (5G -&gt; 4G -&gt; GSM
-&gt; Dead Zone).
 State Management: Local caching of transaction hashes during downtime.
 Reconciliation API: Handshakes with the core engine to push batched proofs when
connectivity is restored.
2. The Opportunistic Sync Engine (Core)
 Protocol Switching: Automated fallback logic (Patent-Pending INPI 120488).
 Conflict Resolution: Cryptographic verification of offline data to prevent double-
spending or data corruption upon mainnet sync.
Integration (Coming Soon)
The public SDK is currently undergoing closed beta testing with select DePIN partners on
IoTeX.
Example Usage (Pseudo-code)
import { WedeClient } from &#39;@wede/sdk&#39;;

const wede = new WedeClient({
chainId: 4689, // IoTeX Mainnet

fallbackMode: &#39;agressive&#39; // Trigger sync on signal degradation
});

wede.on(&#39;connectivity_loss&#39;, async (localState) =&gt; {
console.log(&#39;Switching to Offline Consensus Mode&#39;);
await wede.lockState(localState);
});

Contact
For access to the Private Beta or integration inquiries, please contact
grants@wede.pt
