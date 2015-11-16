---
layout: post
title: Taming TestFlight
date: 2014-01-05 10:23:21.000000000 -06:00
summary: While TestFlight is an incredibly useful service, it has been a bit of a skirmish for me to get around. The workflow can be very convoluted. I am not sure it is my own dense brain or the process is indeed intricate. So, I wanted to write a guide for my own reference and for new developers.
---

**UPDATE**: This document referes to TestFlight, the service found at [www.testflightapp.com](https://www.testflightapp.com/) and not Apple's beta testing service, [TestFlight Beta Testing](https://developer.apple.com/testflight/)
<br />

<p>While <a href="http://help.testflightapp.com/customer/portal/articles/1352859-getting-started-as-a-developer">TestFlight</a> is an incredibly useful service, it has been a bit of a skirmish for me to get around. The workflow can be very convoluted. I am not sure it is my own dense brain or the process is indeed intricate. So, I wanted to write a guide for my own reference and for new developers.</p>

<p>First, here are TestFlight&#8217;s guides for getting started:</p>

<ul>
<li><a href="http://help.testflightapp.com/customer/portal/articles/1352859-getting-started-as-a-developer">TestFlight | Getting started as a Developer</a></li>
<li><a href="http://help.testflightapp.com/customer/portal/articles/1339397-getting-started-as-a-tester">TestFlight | Getting started as a Tester</a></li>
</ul>

<p>However there are caveats, from Apple&#8217;s as well as TestFlight&#8217;s side which make the process a pain in the butt! So, here is the workflow that works for me. This is being written from the perspective of a developer.</p>

<ol>
<li>Setup

<ol>
<li>If you don&#8217;t have a TF account, create one → <a href="https://testflightapp.com/register/">TestFlight » Beta Testing On The Fly</a>. If you have a tester account, flip the switch in &#8216;Account Settings&#8217; to allow access to developer features → <a href="https://testflightapp.com/account/">TestFlight » Your Account</a>.</li>
<li>Create a team if you don&#8217;t have one already. All apps uploaded to a team will be visible to all the team members. However, you can configure access to build granularly, as I discuss in 3.2.</li>
<li>In your Xcode project, add and enable TF SDK → <a href="https://testflightapp.com/sdk/download/">TestFlight » SDK</a>. Follow the instructions that ship in &#8216;Readme.md&#8217;.</li>
</ol></li>
<li>Generating and uploading a build

<ol>
<li>Set the deployment device to <em>iOS Device</em> in Xcode.</li>
<li>Then archive a build. <strong>Product » Archive</strong>. If the build fails with an error about missing provisioning profile, set the appropriate <strong>team</strong> profile here: <strong>Build Setting » Code Signing » Provisioning Profile</strong>. If you set a distribution profile, TF will reject the build.</li>
<li>Once the build is archived, organizer will pop-up: <strong>Distribute » Save For Enterprise or Ad Hoc Deployment</strong>.</li>
<li>Having generated the IPA, upload it to TF → <a href="https://testflightapp.com/dashboard/">TestFlight » Dashboard</a>. You can also use their desktop app → <a href="https://testflightapp.com/dashboard/tools">TestFlight » Tools</a>.</li>
</ol></li>
<li>What devices have access?

<ol>
<li>TF can read the provisioning profile that is embedded in your uploaded IPA. So, all the devices you have in you provisioning portal at the time of generating the IPA will show up in TF. Those devices which have associated TF accounts appear as testers&#8217; names with device details, others will be just UDIDs.</li>
<li>To see all the devices in the current profile follow these breadcrumbs: <strong><a href="https://testflightapp.com/dashboard/applications/">Apps</a> » Your App » Build » Permissions (in the left-sidebar)</strong>. Here you can granularly configure access.</li>
</ol></li>
<li>Inviting testers

<ol>
<li>TF cannot directly add or modify devices in your developer account. However, it does send you a nice email with UDID and other device info from testers which you can use to add devices to the developer portal.</li>
<li>Invite new testers via TF → <a href="https://testflightapp.com/dashboard/team/members/add/">TestFlight » Add a Teammate</a>. Better than sending emails is just sharing recruitment links. Grab it here → <a href="https://www.testflightapp.com/dashboard/team/recruitment/edit">TestFlight » Recruitment</a></li>
<li>They will receive an email with an invite which they can follow to create a new account and/or install your provisioning profile on their device. Once they do so, you&#8217;ll receive an email with their device details. Sometimes, this can take a while; you need to wait this out or ask testers to send you their UDIDs manually<a href="#fn:1" id="fnref:1" title="see footnote" class="footnote">[1]</a>.</li>
<li>Add the device(s) to provisioning portal → <a href="https://developer.apple.com/account/ios/device/deviceList.action">iOS Devices - Apple Developer</a>. You can upload the file(s) TF sent you in the email.</li>
<li>Now, your new testers will show up in TF under <em>Teammate Devices Not On This Profile</em>. Apps will start showing up for new testers but they will be denied installation.</li>
</ol></li>
<li>Adding testers to profile

<ol>
<li>The simplest way to add new testers to a TF profile is to upload a new build after refreshing Xcode<a href="#fn:2" id="fnref:2" title="see footnote" class="footnote">[2]</a>. To refresh Xcode: <strong>Preferences » Accounts » Select your Apple ID » View Details » Refresh arrow</strong>. Now generate a new IPA and upload it to TF. On the <em>Permissions</em> page for your build, check the new devices and voila.. Your testers will now have access (ask them to refresh the TF page in their browser).</li>
<li>If you&#8217;re not ready to upload a new build, you can add new testers by updating the profile in TF.

<ol>
<li>After adding devices in iOS Provisioning Portal, download the updated profile → <a href="https://developer.apple.com/account/ios/profile/profileList.action">iOS Provisioning Profiles - Apple Developer</a>.</li>
<li>In TF, on <em>Permissions</em> page: <strong>Update Profile » Upload</strong>.</li>
<li>Check the new teammates/devices to permit them to install the build.</li>
<li>Ask your testers to refresh TF on their devices and they will be prompted to install a new profile<a href="#fn:3" id="fnref:3" title="see footnote" class="footnote">[3]</a>. Once they do, they can access and install your apps!</li>
<li>You won&#8217;t have to do this for new builds as they will come embedded with these new devices, as detailed in 5.1.</li>
</ol></li>
</ol></li>
</ol>

<p>And that is that. TF is a little overwhelming for new users; I should know! If I missed anything or you need clarification about something, feel free to let me know or ask me <a href="https://twitter.com/gravicle">@gravicle</a>.</p>

<p>Happy building!</p>

<div class="footnotes">
<hr />
<ol>

<li id="fn:1">
<p>Please ask them to not use apps like <a href="https://itunes.apple.com/us/app/udid-sender/id306603975?mt=8">this</a>. iOS 7 onwards Apple has blocked access to UDIDs and all these apps can return are advertising identifiers which are useless for distribution purposes. An alternative is to use iTunes → <a href="http://whatsmyudid.com/">What&#8217;s my UDID?</a>. <a href="#fnref:1" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

<li id="fn:2">
<p>You don&#8217;t <em>have</em> to. The changes might propagate in time, but it sometimes takes a long time for me. Refreshing ensures that new devices are included in the embedded profile. <a href="#fnref:2" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

<li id="fn:3">
<p>Another reason why this route is sub-optimal. <a href="#fnref:3" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

</ol>
</div>
