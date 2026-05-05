---
title: "Anchore Enterprise and the DoD DevSecOps Reference Design"
url: "https://anchore.com/blog/anchore-enterprise-and-the-dod-devsecops-reference-design/"
date: "Tue, 14 Apr 2026 12:00:00 +0000"
author: "Chadd Owen"
feed_url: "https://anchore.com/feed/"
---
The post <a href="https://anchore.com/blog/anchore-enterprise-and-the-dod-devsecops-reference-design/">Anchore Enterprise and the DoD DevSecOps Reference Design</a> appeared first on <a href="https://anchore.com">Anchore</a>.
<p>The DoD, Contractors, and Federal Systems Integrators (FSIs) are increasingly leveraging DevSecOps to iterate and deploy software. As a result, the<a href="https://dodcio.defense.gov/Portals/0/Documents/DoD%20Enterprise%20DevSecOps%20Reference%20Design%20v1.0_Public%20Release.pdf"> DoD DevSecOps Reference Design</a> is the canonical architecture for the entire defense industrial base (DIB). In many cases, it is even contractually required.</p>



<p>The goal of this Reference Design is to automate, monitor, and apply security at all phases of the software development lifecycle. It organizes software development into a (DoD) software factory, which is broken down into distinct phases. Each phase contains specific activities and tools designed to automate security and quality checks. Anchore Enterprise is tightly integrated with these phases, tools, and activities.</p>



<h2 class="wp-block-heading"><a href="https://dodcio.defense.gov/Portals/0/Documents/DoD%20Enterprise%20DevSecOps%20Reference%20Design%20v1.0_Public%20Release.pdf#page=34">Software Factory Tools and Activities &#8211; Section 4.2</a></h2>



<p>The <a href="https://anchore.com/blog/introduction-to-the-dod-software-factory/">DoD software factory</a> relies on integrating security directly into your developer workflows. Anchore Enterprise supports this by acting as a seamless guardrail during the earliest stages of the software lifecycle.</p>



<h3 class="wp-block-heading">The Develop Phase</h3>



<p>A critical requirement during the Develop phase is evaluating source code for vulnerable packages. Anchore Enterprise handles this by generating an<a href="https://anchore.com/sbom/"> SBOM (Software Bill of Materials)</a>. This allows it to deeply scan source code repositories for known vulnerabilities. Using<a href="https://www.google.com/search?q=https://anchore.com/policy-as-code/"> policy-as-code</a>, Anchore can automatically stop CI/CD pipeline build promotions. If vulnerable or non-compliant content is found, risky code never advances to the next stage.</p>



<h3 class="wp-block-heading">The Build Phase</h3>



<p>Managing dependencies and artifact repositories is essential during the Build phase. Anchore generates a comprehensive SBOM from container images, filesystems, VMDKs, and open source code. This helps teams understand and store build dependencies as deliverable artifacts. Additionally, Anchore continuously monitors and scans containers within your artifact repositories. This actively detects vulnerabilities, policy violations, exposed secrets, and malware.</p>



<h3 class="wp-block-heading">The Test Phase</h3>



<p>The Test phase focuses on hardening and ensuring compliance. Anchore provides robust software license compliance checking. It uses policy gates to enforce acceptable use for open source distributions. Anchore also acts as a primary container security tool. It hardens containers to meet Authorizing Official (AO) and regulatory requirements via policy-as-code. You can leverage POA&amp;M-as-code through allowlisting to set time-based dates for authorized exceptions. Furthermore, Anchore scans containers against <a href="https://anchore.com/blog/stig-compliance-requirements/">DISA STIGs</a> and frameworks like <a href="https://anchore.com/compliance/nist/800-53">NIST 800-53</a> or <a href="https://anchore.com/compliance/nist/800-190/">800-190</a>. It generates the necessary artifacts and uses denylisting to ensure only authorized images are utilized.</p>



<h3 class="wp-block-heading">The Release and Deliver Phase</h3>



<p>Before software leaves the factory, a definitive go/no-go decision must be made. Anchore leverages its policy-as-code engine to fully automate this release decision, ensuring that all images pass your organization&#8217;s required gates and contractual policies prior to delivery.</p>



<figure class="wp-block-table"><table class="has-fixed-layout"><thead><tr><th><strong>Phase</strong></th><th><strong>Feature</strong></th><th><strong>Anchore Enterprise Role</strong></th></tr></thead><tbody><tr><td><strong>Develop</strong></td><td>Source Code Evaluation</td><td>Stop vulnerable builds via policy-as-code.</td></tr><tr><td><strong>Build</strong></td><td>Dependency Management</td><td>Generate comprehensive artifact SBOMs.</td></tr><tr><td><strong>Build</strong></td><td>Artifact Repository</td><td>Continuously scan repositories for risks.</td></tr><tr><td><strong>Test</strong></td><td>License Compliance</td><td>Enforce OSS usage policies with policy-as-code.</td></tr><tr><td><strong>Test</strong></td><td>Container Security</td><td>Harden containers &amp; manage exceptions.</td></tr><tr><td><strong>Test</strong></td><td>Container Policy Enforcement</td><td>Enforce STIG/NIST compliance with policy-as-code.</td></tr><tr><td><strong>Release and Deliver</strong></td><td>Release go/no-go decision</td><td>Automatego/no-go decision with policy-as-code.</td></tr></tbody></table></figure>



<h2 class="wp-block-heading"><a href="https://dodcio.defense.gov/Portals/0/Documents/DoD%20Enterprise%20DevSecOps%20Reference%20Design%20v1.0_Public%20Release.pdf#page=46">Production Operation Tools and Activities &#8211; Section 4.3</a></h2>



<p>Once software moves beyond the factory, maintaining visibility and security in production environments is just as critical.</p>



<h3 class="wp-block-heading">The Deploy Phase</h3>



<p>During deployment, Anchore ensures smooth and secure delivery of containers to the registry. It generates the necessary SBOMs, vulnerability reports, and STIG outputs directly to an artifact repository and pushes the validated container to the applicable registry, providing these as artifacts to assessors. Once deployed, Anchore performs post-deployment security scans on running images using Kubernetes or Amazon ECS runtimes to continually check for vulnerabilities and compliance. You can also use application groups to monitor downstream releases over time and alert when new CVEs are discovered.</p>



<h3 class="wp-block-heading">The Operate Phase</h3>



<p>Continuous assessment is key in the Operate phase. Anchore provides a comprehensive supply chain security operations dashboard for this exact purpose. It continuously assesses and alerts on your Kubernetes container security posture. This maintains visibility over any container within the Anchore Enterprise SBOM inventory.</p>



<h3 class="wp-block-heading">The Monitor Phase</h3>



<p><a href="https://anchore.com/blog/guide-to-continuous-compliance-monitoring/">Continuous monitoring</a> forms the backbone of production security. Anchore facilitates Information Security Continuous Monitoring (ISCM). It actively detects security and compliance violations, generates findings, and provides actionable recommendations. It also offers comprehensive alerting and notification capabilities. Security personnel are immediately notified about policy violations and new CVEs across containers, open source code, and imported SBOMs. Finally, Anchore helps maintain an accurate asset inventory. It utilizes Kubernetes runtime inventory to monitor all deployed images across your clusters.</p>



<figure class="wp-block-table"><table class="has-fixed-layout"><thead><tr><th><strong>Phase</strong></th><th><strong>Feature</strong></th><th><strong>Anchore Enterprise Role</strong></th></tr></thead><tbody><tr><td><strong>Deploy</strong></td><td>Deliver Containers</td><td>Push validated images &amp; artifacts to registries.</td></tr><tr><td><strong>Deploy</strong></td><td>Post-Deployment Scan</td><td>Scan running images (K8s/ECS).&nbsp;</td></tr><tr><td><strong>Operate</strong></td><td>Operations Dashboard</td><td>Assess continuous K8s security posture.</td></tr><tr><td><strong>Monitor</strong></td><td>Information Security Continuous Monitoring (ISCM)</td><td>Detect violations &amp; generate findings.</td></tr><tr><td><strong>Monitor</strong></td><td>Alerting and Notification</td><td>Notify on new CVEs &amp; policy violations.</td></tr><tr><td><strong>Monitor</strong></td><td>Asset Inventory</td><td>Track deployed images via Kubernetes runtime inventory.</td></tr></tbody></table></figure>



<p></p>



<h2 class="wp-block-heading">Next Steps: Securing Your Software Factory</h2>



<p>Aligning your software factory with the DoD DevSecOps Reference Design doesn&#8217;t have to be a manual, spreadsheet-heavy burden. With the right automated guardrails, you can accelerate software delivery without compromising on federal security standards.</p>



<p>Here is how you can get started:</p>



<ol class="wp-block-list">
<li><strong>Assess Your Current Pipeline:</strong> Identify existing gaps in your source code evaluation and container scanning processes.</li>



<li><strong>Implement Policy-as-Code:</strong> Define your security rules centrally so that non-compliant or vulnerable builds are stopped automatically.</li>



<li><strong>Deploy Automated Guardrails:</strong> Integrate continuous scanning directly into your tools to meet DoD Reference Design requirements.</li>
</ol>



<p><a href="https://anchore.com/contact-us">Get in touch with the Anchore Federal Team</a> to discuss how we can help secure your DevSecOps pipelines.</p>
