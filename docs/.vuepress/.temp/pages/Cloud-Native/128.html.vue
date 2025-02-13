<template><div><h1 id="_128-automate-multi-architecture-image-build-for-openkf-and-push-to-multiple-image-repositories" tabindex="-1"><a class="header-anchor" href="#_128-automate-multi-architecture-image-build-for-openkf-and-push-to-multiple-image-repositories" aria-hidden="true">#</a> 128: Automate Multi-Architecture Image Build for <code v-pre>openkf</code> and Push to Multiple Image Repositories</h1>
<p><strong>Description:</strong></p>
<p>To meet the requirements of a diverse set of users, we aim to automate the process of building the <code v-pre>openkf</code> Docker images for various architectures and push them to multiple image repositories seamlessly.</p>
<p><strong>Objective:</strong></p>
<ul>
<li>Automatically build Docker images of <code v-pre>openkf</code> for <code v-pre>linux/amd64</code> and <code v-pre>linux/arm64</code> architectures.</li>
<li>Push the images to Docker Hub, AliYun Docker Hub, and GitHub Container Registry.</li>
</ul>
<p><strong>Tasks:</strong></p>
<ol>
<li><strong>Setup Multi-Architecture Build System</strong>
<ul>
<li>Use GitHub Actions with QEMU and Docker Buildx to support multi-architecture builds for <code v-pre>linux/amd64</code> and <code v-pre>linux/arm64</code>.</li>
<li>On every new release, commit to the <code v-pre>main</code> branch, or scheduled event, trigger the build process.</li>
</ul>
</li>
<li><strong>Support Multiple Image Repositories</strong>
<ul>
<li>Docker Hub: Push to <code v-pre>openim/openkf-server</code>.</li>
<li>AliYun Docker Hub: Push to <code v-pre>registry.cn-hangzhou.aliyuncs.com/openimsdk/openkf-server</code>.</li>
<li>GitHub Container Registry: Push to <code v-pre>ghcr.io/openimsdk/openkf-server</code>.</li>
</ul>
</li>
<li><strong>Dynamic Image Tagging</strong>
<ul>
<li>Use Docker Metadata Action to generate dynamic tags based on events such as scheduled triggers, branch commits, pull requests, semantic versioning, and the commit SHA.</li>
<li>Ensure the built image does not get pushed during pull request events.</li>
</ul>
</li>
<li><strong>Authentication &amp; Security</strong>
<ul>
<li>Configure authentication for Docker Hub, AliYun, and GitHub Container Registry using secrets.</li>
<li>Ensure a secure and seamless push operation for each repository.</li>
</ul>
</li>
<li><strong>Notifications &amp; Logging</strong>
<ul>
<li>Send notifications to the development team in case of any build or push failures through GitHub Actions.</li>
<li>Maintain logs for every build and push operation for traceability.</li>
</ul>
</li>
</ol>
<p><strong>Acceptance Criteria:</strong></p>
<ul>
<li>The <code v-pre>openkf</code> image should be built successfully for both <code v-pre>linux/amd64</code> and <code v-pre>linux/arm64</code> architectures.</li>
<li>Upon successful build, the image should be available on Docker Hub, AliYun Docker Hub, and GitHub Container Registry.</li>
<li>Properly tagged images based on the defined events and attributes.</li>
<li>No manual intervention required during the entire process.</li>
</ul>
<p><strong>Additional Notes:</strong></p>
<ul>
<li>The automation process is defined in the GitHub Actions workflow. Ensure to review and update the workflow as needed.</li>
<li>Make sure to test the process in a separate branch or environment to avoid disruptions.</li>
</ul>
<p>Feedback and further recommendations are welcome.</p>
</div></template>


