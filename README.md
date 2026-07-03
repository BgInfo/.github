<p align="center">
  <img src="https://img.shields.io/github/v/release/BgInfo/BgInfo?label=Latest%20Version&style=for-the-badge&color=blue" alt="Latest Version" />
  <img src="https://img.shields.io/github/downloads/BgInfo/BgInfo/total?label=Total%20Downloads&style=for-the-badge&color=green" alt="Total Downloads" />
  <img src="https://img.shields.io/github/release-date/BgInfo/BgInfo?label=Release%20Date&style=for-the-badge&color=orange" alt="Release Date" />
  <img src="https://img.shields.io/badge/Platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="Windows" />
  <img src="https://img.shields.io/badge/License-Free-brightgreen?style=for-the-badge" alt="Free" />
  <img src="https://img.shields.io/badge/Installer-MSI-red?style=for-the-badge" alt="MSI Installer" />
</p>

<h1 align="center">BgInfo — Free Desktop Background System Information Tool for Windows</h1>

<p align="center">
  <a href="https://github.com/BgInfo/BgInfo/releases/latest"><img src="https://img.shields.io/badge/⬇_DOWNLOAD_LATEST_MSI-blue?style=for-the-badge&logoColor=white" alt="Download BgInfo MSI" /></a>
  <a href="https://github.com/BgInfo/BgInfo/releases"><img src="https://img.shields.io/badge/📦_ALL_RELEASES-gray?style=for-the-badge" alt="All Releases" /></a>
</p>

---

<p><strong>BgInfo</strong> is a free, lightweight Windows utility that automatically displays essential system information — IP address, computer name, OS version, memory, disk space, and more — directly on the desktop wallpaper. Designed for IT administrators, system engineers, and helpdesk teams who manage multiple workstations and servers, BgInfo eliminates the need to manually check each machine's configuration. It is part of the <strong>Microsoft Sysinternals</strong> suite and runs as a portable, no-install tool.</p>

<h2>Download BgInfo</h2>

<table>
  <tr>
    <th>File</th>
    <th>Architecture</th>
    <th>Type</th>
    <th>Link</th>
  </tr>
  <tr>
    <td><strong>BgInfo_Setup.msi</strong></td>
    <td>64-bit (x64)</td>
    <td>MSI Installer</td>
    <td><a href="https://github.com/BgInfo/BgInfo/releases/latest">⬇ Download</a></td>
  </tr>
  <tr>
    <td><strong>BgInfo_Setup_x86.msi</strong></td>
    <td>32-bit (x86)</td>
    <td>MSI Installer</td>
    <td><a href="https://github.com/BgInfo/BgInfo/releases/latest">⬇ Download</a></td>
  </tr>
</table>

<blockquote>
  <p>All releases are available on the <a href="https://github.com/BgInfo/BgInfo/releases"><strong>Releases</strong></a> page. Each release includes SHA-256 checksums for verification.</p>
</blockquote>

<h2>Key Features</h2>

<ul>
  <li><strong>Desktop wallpaper overlay</strong> — renders system details directly onto the desktop background without additional windows or taskbar clutter</li>
  <li><strong>Comprehensive system data</strong> — displays computer name, IP address, MAC address, subnet mask, default gateway, DNS servers, OS version, service pack, domain name, logon server, CPU type, RAM, disk space, and uptime</li>
  <li><strong>Custom fields</strong> — add your own data sources using WMI queries, VBScript, environment variables, or registry keys</li>
  <li><strong>Group Policy and logon script integration</strong> — deploy across hundreds of machines via Active Directory GPO or startup/logon scripts for hands-free configuration</li>
  <li><strong>Portable mode</strong> — run from a USB drive, network share, or any directory without installation</li>
  <li><strong>Multiple monitor support</strong> — display information across all connected displays</li>
  <li><strong>Bitmap output</strong> — export the generated background as a BMP file for documentation or remote viewing</li>
  <li><strong>Silent mode</strong> — apply settings without user interaction using command-line switches for automated deployments</li>
  <li><strong>Fully customizable layout</strong> — adjust font, color, position, and opacity of the information overlay to match any wallpaper</li>
</ul>

<h2>How It Works</h2>

<p>BgInfo reads system information at startup (or on demand), renders it as text onto a copy of the current desktop wallpaper, and sets the result as the new background image. The process is instant and consumes no ongoing CPU or memory resources after the wallpaper is applied.</p>

<h3>Quick Start — Single Machine</h3>

<ol>
  <li>Download the <strong>MSI installer</strong> from the <a href="https://github.com/BgInfo/BgInfo/releases/latest">latest release</a></li>
  <li>Run the installer or extract and launch <strong>BgInfo.exe</strong> directly</li>
  <li>Select which fields to display in the configuration editor</li>
  <li>Click <strong>Apply</strong> — your desktop background is immediately updated with system information</li>
</ol>

<h3>Silent MSI Installation (Enterprise)</h3>

<pre><code>msiexec /i BgInfo_Setup.msi /qn /norestart</code></pre>

<h3>Enterprise Deployment — Active Directory GPO</h3>

<ol>
  <li>Place <strong>BgInfo.exe</strong> and your saved <strong>.bgi</strong> configuration file on a network share accessible by all target machines</li>
  <li>Create a Group Policy Object that runs BgInfo at user logon:
    <code>\\server\share\BgInfo64.exe \\server\share\config.bgi /timer:0 /silent /nolicprompt</code></li>
  <li>Link the GPO to the appropriate Organizational Unit (OU)</li>
  <li>Every user who logs in will see the configured system information on their desktop</li>
</ol>

<h3>Logon Script Deployment</h3>

<ol>
  <li>Add BgInfo to a batch or PowerShell logon script with the <code>/timer:0</code> and <code>/silent</code> flags</li>
  <li>Point to a centralized <strong>.bgi</strong> configuration file on a shared network path</li>
  <li>BgInfo applies the wallpaper silently during each logon without user intervention</li>
</ol>

<h2>Command-Line Reference</h2>

<table>
  <tr>
    <th>Switch</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>/timer:0</code></td>
    <td>Apply settings immediately without showing the countdown dialog</td>
  </tr>
  <tr>
    <td><code>/silent</code></td>
    <td>Suppress error messages during execution</td>
  </tr>
  <tr>
    <td><code>/nolicprompt</code></td>
    <td>Skip the license agreement prompt on first run</td>
  </tr>
  <tr>
    <td><code>/popup</code></td>
    <td>Display information in a popup window instead of the wallpaper</td>
  </tr>
  <tr>
    <td><code>/taskbar</code></td>
    <td>Display information in the taskbar notification area</td>
  </tr>
  <tr>
    <td><code>/all</code></td>
    <td>Apply to all logged-on user sessions on a Terminal Server</td>
  </tr>
  <tr>
    <td><code>/log</code></td>
    <td>Write errors to the specified log file</td>
  </tr>
  <tr>
    <td><code>/rtf</code></td>
    <td>Export configuration to an RTF file</td>
  </tr>
</table>

<h2>Available Information Fields</h2>

<p>BgInfo can display any combination of the following system properties on the desktop background:</p>

<table>
  <tr>
    <th>Category</th>
    <th>Fields</th>
  </tr>
  <tr>
    <td>Network</td>
    <td>IP Address, MAC Address, Subnet Mask, Default Gateway, DNS Server, DHCP Server, Network Card, Domain Name</td>
  </tr>
  <tr>
    <td>System</td>
    <td>Computer Name, OS Version, Service Pack, Build Number, Boot Time, System Uptime, Logon Domain, Logon Server, User Name</td>
  </tr>
  <tr>
    <td>Hardware</td>
    <td>CPU Type, CPU Speed, Number of Processors, Total RAM, Free RAM, Disk Space (Free/Total per volume), System Manufacturer, System Model, BIOS Version, Serial Number</td>
  </tr>
  <tr>
    <td>Custom</td>
    <td>WMI Queries, VBScript Output, Environment Variables, Registry Values, File Contents</td>
  </tr>
</table>

<h2>System Requirements</h2>

<table>
  <tr>
    <th>Requirement</th>
    <th>Details</th>
  </tr>
  <tr>
    <td>Operating System</td>
    <td>Windows 7 / 8 / 10 / 11 / Server 2008–2025 (32-bit and 64-bit)</td>
  </tr>
  <tr>
    <td>Price</td>
    <td>Free</td>
  </tr>
  <tr>
    <td>Installation</td>
    <td>MSI installer or portable — no installation required</td>
  </tr>
  <tr>
    <td>Dependencies</td>
    <td>None — standalone executable</td>
  </tr>
  <tr>
    <td>Enterprise Deployment</td>
    <td>Active Directory Group Policy, logon scripts, SCCM, Intune</td>
  </tr>
</table>

<h2>Common Use Cases</h2>

<ul>
  <li><strong>Server room identification</strong> — instantly see server name, IP address, and role on the desktop when connecting via RDP or KVM</li>
  <li><strong>Helpdesk support</strong> — ask users to read system details directly from their wallpaper instead of navigating through system settings</li>
  <li><strong>IT asset management</strong> — display asset tags, serial numbers, and warranty information alongside system specs</li>
  <li><strong>Lab and classroom management</strong> — identify workstations by name and IP address across large computer labs</li>
  <li><strong>Compliance and auditing</strong> — show OS patch level, domain membership, and last boot time for quick visual verification</li>
  <li><strong>Remote Desktop sessions</strong> — immediately identify which server or workstation you are connected to in multi-session environments</li>
  <li><strong>Virtual machine identification</strong> — distinguish between multiple VMs running on the same hypervisor host</li>
</ul>

<h2>Alternatives to BgInfo</h2>

<p>If you are looking for similar <strong>desktop system information tools</strong>, consider these alternatives:</p>

<ul>
  <li><strong>Rainmeter</strong> — customizable desktop widget platform that can display system stats, weather, and more</li>
  <li><strong>Samurize</strong> — desktop enhancement tool with system monitoring widgets</li>
  <li><strong>Conky</strong> — lightweight system monitor for Linux desktops with customizable display</li>
  <li><strong>HWiNFO</strong> — in-depth hardware analysis and monitoring tool for Windows</li>
  <li><strong>Speccy</strong> — system information tool that provides detailed hardware and software specs</li>
  <li><strong>CPU-Z</strong> — focused hardware identification utility for CPU, memory, and motherboard details</li>
  <li><strong>Open Hardware Monitor</strong> — free, open-source hardware monitoring tool with sensor data</li>
</ul>

<h2>Frequently Asked Questions</h2>

<h3>How do I download BgInfo?</h3>
<p>Go to the <a href="https://github.com/BgInfo/BgInfo/releases/latest"><strong>Releases</strong></a> page and download the latest <strong>MSI installer</strong> for your system architecture (x64 or x86).</p>

<h3>How do I make BgInfo run automatically at startup?</h3>
<p>Place a shortcut to BgInfo with your <code>.bgi</code> configuration file in the Windows Startup folder, or deploy it via Group Policy logon script with the <code>/timer:0 /silent /nolicprompt</code> switches.</p>

<h3>Does BgInfo consume system resources while running?</h3>
<p>No. BgInfo only runs once to generate and apply the wallpaper, then exits. It does not remain in memory or consume CPU cycles after the background is set.</p>

<h3>Can I use BgInfo on Windows Server?</h3>
<p>Yes. BgInfo is fully compatible with Windows Server 2008, 2012, 2016, 2019, 2022, and 2025, including Server Core and Terminal Server / Remote Desktop Services environments.</p>

<h3>How do I install BgInfo silently via MSI?</h3>
<p>Run <code>msiexec /i BgInfo_Setup.msi /qn /norestart</code> from an elevated command prompt or deploy the MSI package through Group Policy, SCCM, or Intune.</p>

<h3>How do I display custom information?</h3>
<p>In the BgInfo configuration editor, click <strong>Custom</strong> to add fields sourced from WMI queries, VBScript, environment variables, or registry keys. This allows displaying any data that Windows can provide.</p>

<h3>Can I deploy BgInfo with Microsoft Intune or SCCM?</h3>
<p>Yes. Package the MSI installer as a Win32 app in Intune, or distribute it as an SCCM application with the appropriate command-line switches for silent installation.</p>

<h2>Summary</h2>

<p><strong>BgInfo</strong> is the standard tool for displaying system configuration information on Windows desktop backgrounds. Whether you manage a handful of workstations or thousands of servers, BgInfo provides instant visual identification of any machine through a simple, resource-free wallpaper overlay. Its portability, silent deployment options, and deep customization through WMI and scripting make it an indispensable utility for IT professionals worldwide.</p>

<p align="center">
  <a href="https://github.com/BgInfo/BgInfo/releases/latest"><strong>⬇ Download Latest Release</strong></a>
</p>
