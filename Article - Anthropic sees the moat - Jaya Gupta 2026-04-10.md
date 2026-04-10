# Anthropic sees the moat. Do you?

**Source:** Jaya Gupta (@JayaGup10)  
**Date:** 2026-04-10  
**Link:** https://x.com/jayagup10/status/2042401200109408681  

---

## Full Article

Anthropic sees the moat. Do you?

The scarce asset in enterprise AI may be shifting from intelligence to permission. For two years the market competed on model quality: which system was smartest, fastest, most reliable. The models are now good enough that in most enterprise settings the harder question is no longer whether the model can help. It is whether the company will let the model act inside real systems.

Permission here does not mean access controls in the abstract. It means the right to write and merge code, touch production infrastructure, open and close tickets, change system configurations, message customers, approve workflows, and trigger downstream actions across enterprise tools. Before that boundary, the model advises. After it, the model operates.

That shift matters because of a pattern that we have seen in the past tried by the most massive platforms of all time. A company introduces a capability enterprises adopt at scale. That capability creates new governance, security, and operational burdens. The same company is then best positioned to sell the layer that manages those burdens, because it has the deepest integration, the best telemetry, and the most complete view of how the system behaves in practice. Each side of the relationship reinforces the other. Enterprises then go on to buy the governance layer from the same company that sold them the capability, which deepens their dependence on that company across both dimensions. The more they rely on the capability, the more they need governance. The more they rely on the governance, the harder it is to replace the capability.

History shows that every major platform has tried to close the loop. No company running this pattern has ever been able to describe it plainly, because the honest version sounds extractive: we created the capability, it generates complexity and governance burdens, and we are best positioned to monetize both. So the public language stays at enablement, safety, and reduced complexity. The strategic reality is visible mainly in hindsight.

The historical examples are worth understanding, but they are not all the same:

**Google** — The clearest case of redefining the control layer around an infrastructure you helped build. They built the advertising machinery of the internet, the systems that tracked what users did across websites, matched them to audiences, and let advertisers follow them around the web. When regulators and browsers started blocking that tracking, Google did not step aside. It proposed replacing third-party cookies with its own Privacy Sandbox: new APIs, controlled by Google, that let advertisers do much of the same targeting inside a "privacy-preserving" framework. The company that built the tracking economy became the company writing the rules for what came after it. The loop closed because Google made itself the only realistic path through the transition.

**Microsoft** — Shows how the loop works at the identity layer. Entra ID anchors the access surface enterprises use to govern who can reach what — on-prem systems, cloud applications, devices. Microsoft then sells the security and governance stack defending that same surface: identity threat detection, conditional access policies, privileged identity management, and now AI-driven security workflows through Security Copilot. The connection is direct: owning the identity layer means owning the most valuable telemetry in the enterprise, which makes Microsoft's security products structurally easier to justify than best-of-breed alternatives operating with less context.

**AWS and Palantir** — Versions of the same dynamic. AWS moved enterprises' computing into Amazon's cloud, then built a large business selling the governance, compliance, and security tooling those same enterprises needed to operate safely there. Palantir went deeper into fewer places — embedding itself in the sensitive decision workflows of governments and large institutions, then making its accredited, secure operating environment inseparable from the capability itself.

What makes AI different is that every prior loop was sequential — this one compounds. In each of the earlier examples, the capability and the threat were separable. Google's tracking infrastructure was not itself the attacker. Microsoft's identity layer was not itself breaching enterprise systems. AWS's cloud was not the malware. There was always a meaningful gap between the product and the harm it might enable.

Frontier AI closes that gap. Anthropic said this directly about Mythos (latest model): "The same improvements that make the model substantially more ef..."

---

## Summary

Enterprise AI is undergoing a strategic shift — the real competition is no longer about who has the smartest model, but who gets permission to act inside enterprise systems. Once a model earns the right to execute (write code, change configs, trigger workflows), the same company that provided the capability becomes the natural seller of the governance layer needed to manage it. History proves this pattern: Google did it with advertising tracking, Microsoft with identity (Entra → Security Copilot), AWS with cloud infrastructure. AI accelerates this loop because the capability and the risk are no longer separable — the same model that advises can also act, meaning governance isn't optional overhead but a structural requirement that follows naturally from adoption.

---

## Key Takeaways

1. **Intelligence is becoming commoditized** — models are "good enough" for most enterprise tasks; the scarce resource is now authorization to act, not capability to think
2. **The platform loop** — sell capability → it creates governance burdens → sell the governance layer → deeper dependence → harder to replace both
3. **Historical precedents** — Google (ads→Privacy Sandbox), Microsoft (Entra→Security Copilot), AWS (cloud→security stack), Palantir (workflows→secure environment)
4. **AI compounds the pattern** — unlike prior loops, the capability and threat are not separable; the model that advises can also act, making governance a structural necessity
5. **Transparency problem** — no company can honestly describe this loop because the plain version sounds extractive, so public language stays at "enablement" and "safety"
6. **Anthropic/Mythos** — specifically called out for bridging the capability-threat gap that prior platforms kept separate

---

## Hermes-Related Interest

High relevance. As an AI agent running in enterprise contexts, this is the exact moat conversation that determines whether agents like Hermes get "act" permissions or stay stuck at "advise." The article's core thesis — that the real battle is over authorization to trigger downstream actions — is the same battle Hermes faces when trying to actually do things (write files, run terminal commands, manage the vault). The compounding risk the article identifies (capability + threat in one system) also describes the trust problem with autonomous agents: the same capabilities that make them useful also make them risky, which creates the governance burden that could end up being monetized by the same company that built the agent. This is directly relevant to how Hermes positions itself in the agent ecosystem.