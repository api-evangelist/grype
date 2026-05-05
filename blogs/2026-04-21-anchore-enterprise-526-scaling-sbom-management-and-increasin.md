---
title: "Anchore Enterprise 5.26: Scaling SBOM Management and Increasing Ecosystem Coverage"
url: "https://anchore.com/blog/anchore-enterprise-5-26/"
date: "Tue, 21 Apr 2026 12:00:00 +0000"
author: "teamanchore"
feed_url: "https://anchore.com/feed/"
---
The post <a href="https://anchore.com/blog/anchore-enterprise-5-26/">Anchore Enterprise 5.26: Scaling SBOM Management and Increasing Ecosystem Coverage</a> appeared first on <a href="https://anchore.com">Anchore</a>.
<p>Modern software supply chains are increasingly complex, spanning a multitude of operating systems, architectures, and external vendor dependencies. As organizations mature their DevSecOps practices, the challenge has shifted from simply generating Software Bills of Materials (SBOMs) to managing them at scale and extracting actionable security insights across every environment.</p>



<p>With the release of Anchore Enterprise 5.26, we are reinforcing our commitment to:</p>



<ul class="wp-block-list">
<li>comprehensive supply chain visibility,</li>



<li>scalable SBOM operations, and</li>



<li>frictionless shift-left security tooling.</li>
</ul>



<p>This release brings deeper vulnerability insights into diverse operating systems, enhanced tools for managing massive SBOM inventories, and improved reporting capabilities placed directly at the developer&#8217;s fingertips.</p>



<p>Here is a closer look at what is new in Anchore Enterprise 5.26:</p>



<h2 class="wp-block-heading">Expanded Ecosystem Visibility: Fedora and VMware PhotonOS Feeds</h2>



<p>As organizations diversify their infrastructure, their security tools must keep pace with highly specialized operating systems that do not operate under standard rules. Relying on generic vulnerability matching for these environments often leads to noisy, inaccurate reporting. For example, Fedora’s rapid release cycle and bleeding-edge packages mean standard enterprise feeds frequently lag behind, leading to mismatched package states. Conversely, VMware PhotonOS is a minimalist OS optimized for container infrastructure; generic feeds often assume a full Linux footprint, resulting in a flood of false positives for its stripped-down environment.</p>



<p>To solve this, Anchore Enterprise 5.26 introduces native, dedicated vulnerability data feeds specifically tailored to the unique lifecycles of the Fedora and VMware PhotonOS ecosystems. By pulling directly from these authoritative native feeds, Anchore deeply understands the specific composition and patch states of these distinct distributions. Customers generating SBOMs with these packages will now receive highly accurate security vulnerability reporting that cuts through the noise, minimizes false positives, and aligns with the actual patch management realities of their infrastructure.</p>



<h2 class="wp-block-heading">Vulnerability Matching for Arch Linux and SecureOS</h2>



<p>Much like the need for dedicated feeds for Fedora and PhotonOS, securing other open source operating systems requires a tailored approach. Arch Linux, for instance, operates on a continuous rolling release model, completely lacking the discrete version numbers that generic scanners rely on to track CVEs. Similarly, SecureOS utilizes hardened, custom package architectures that standard matching rules frequently misinterpret, leaving critical security blind spots.</p>



<p>To solve these unique structural challenges, Anchore Enterprise 5.26 adds new data sources and introduces novel vulnerability matching algorithms for these environments. Rather than trying to force rolling releases or custom architectures into a traditional mold, Anchore has engineered specific logic to track Arch&#8217;s continuous updates and SecureOS’s strict configurations. This ensures that generated SBOMs are analyzed accurately and allows teams to utilize these secure distributions with the exact same automated governance as they are accustomed to.</p>



<h2 class="wp-block-heading">Annotation Filtering for Imported SBOMs (BYOS)</h2>



<p>For the past few years, the industry has been learning to walk. The focus has been on installing SBOM generators, fulfilling basic compliance requirements, and creating baseline software inventories. Now, organizations are poised to take the next step in software supply chain security: actively managing, organizing, and governing those SBOMs at an enterprise scale. As the sheer volume of external &#8220;Bring Your Own SBOMs&#8221; (BYOS) imported into Anchore Enterprise grows (originating from upstream vendors, open-source projects, and other SCA tools), identifying specific SBOMs of interest becomes a needle in a haystack.</p>



<p>To support this next phase of SBOM maturity, Anchore Enterprise 5.26 introduces annotation filtering. Users can now define filters based on imported SBOM annotations using custom key-value pairs. This allows platform engineers and security teams to use custom metadata as criteria to instantly locate, organize, and govern imported SBOMs (e.g., <code>team=backend</code>, <code>environment=production</code>, or <code>vendor=acmecorp</code>). By applying these filters, you can seamlessly integrate 3rd-party SBOMs into your active compliance and risk management workflows without getting buried in data.</p>



<h2 class="wp-block-heading">Shift-Left Frictionless Reporting: HTML Output for AnchoreCTL</h2>



<p>Integrating security into CI/CD pipelines requires tooling that serves both automated systems and the humans who evaluate them. Anchore Enterprise 5.26 introduces a new human-readable HTML output option for the <code>anchorectl image check, image vuln, and image one-time scan</code> commands.</p>



<p>Modern compliance frameworks standardly require reports that serve as official attestations of compliance. To satisfy auditors when they certify an organization, teams need a user-friendly format that can be easily stashed alongside a build as a reliable record of compliance checks. This ensures that clear documentation is always available for review, eliminating the need to translate machine-readable pipeline data (like JSON) through complex scripting, manual intervention, or entirely separate workflow steps.</p>



<p>Now, developers can generate an intuitive, easily shareable HTML compliance report directly from the CLI. This update pushes Anchore further toward the <a href="https://anchore.com/blog/compliance-isnt-an-annual-ritual-anymore/">CompOps</a> ideal of continuous, automated compliance throughout the entire development lifecycle. By seamlessly generating both automated policy gates and human-auditable attestations within the exact same workflow step, organizations can reduce friction and satisfy auditor requirements without slowing down engineering.</p>



<div class="wp-block-kevinbatdorf-code-block-pro"><span><svg height="14" viewBox="0 0 54 14" width="54" xmlns="http://www.w3.org/2000/svg"><g fill="none" fill-rule="evenodd" transform="translate(1 1)"><circle cx="6" cy="6" fill="#FF5F56" r="6" stroke="#E0443E" stroke-width=".5"></circle><circle cx="26" cy="6" fill="#FFBD2E" r="6" stroke="#DEA123" stroke-width=".5"></circle><circle cx="46" cy="6" fill="#27C93F" r="6" stroke="#1AAB29" stroke-width=".5"></circle></g></svg></span><span class="code-block-pro-copy-button" style="color: #e1e4e8; display: none;" tabindex="0"><pre class="code-block-pro-copy-button-pre"><textarea class="code-block-pro-copy-button-textarea" readonly="readonly" tabindex="-1">anchorectl image check my-image:latest --output html > 
compliance-report.html</textarea></pre><svg fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path class="with-check" d="M4.5 12.75l6 6 9-13.5" stroke-linecap="round" stroke-linejoin="round"></path><path class="without-check" d="M16.5 8.25V6a2.25 2.25 0 00-2.25-2.25H6A2.25 2.25 0 003.75 6v8.25A2.25 2.25 0 006 16.5h2.25m8.25-8.25H18a2.25 2.25 0 012.25 2.25V18A2.25 2.25 0 0118 20.25h-7.5A2.25 2.25 0 018.25 18v-1.5m8.25-8.25h-6a2.25 2.25 0 00-2.25 2.25v6" stroke-linecap="round" stroke-linejoin="round"></path></svg></span><pre class="shiki github-dark" style="background-color: #24292e;" tabindex="0"><code><span class="line"><span style="color: #E1E4E8;">anchorectl image check my</span><span style="color: #F97583;">-</span><span style="color: #B392F0;">image</span><span style="color: #E1E4E8;">:latest </span><span style="color: #F97583;">--</span><span style="color: #E1E4E8;">output html </span><span style="color: #F97583;">&gt;</span><span style="color: #E1E4E8;"> </span></span>
<span class="line"><span style="color: #E1E4E8;">compliance</span><span style="color: #F97583;">-</span><span style="color: #E1E4E8;">report.html</span></span></code></pre></div>



<p></p>



<h2 class="wp-block-heading">Take Control of Your Supply Chain</h2>



<p>Anchore Enterprise 5.26 equips teams with the broader ecosystem support, scalable SBOM management, and developer-friendly reporting needed to secure modern software supply chains.</p>



<p><strong>Ready to get started?</strong></p>



<p>Upgrade to Anchore Enterprise 5.26 today to take advantage of these new capabilities. For detailed instructions, API updates, and full release notes, please visit our <a href="https://docs.anchore.com/current/">documentation</a> or reach out to your account team to <a href="https://anchore.com/contact-us">schedule a demo</a>.</p>
