---
layout: post
title:  "Avid/C300 Workflow"
date:   2013-08-20 21:00:00
tags:   reidransom editing
---

I’ve been working with C300 footage in Avid Media Composer for almost a year now so I thought it would be a good idea to share my established workflow and experiences.

My favorite aspect to working with C300 footage is the Canon XF codec.  The bitrates are a fraction of the size of DNxHD or ProRes and Media Composer has excellent native support.  This means the ingest is super quick and there’s no need for an offline/online workflow.

### Card Structure

A good first step is to make sure your folder structure is intact.  It should look something like this:

	CARDROOT/
		CONTENTS/
			CLIPS001/
				A10091/
					A10091.CIF
					A10091.CPF
					A10091.XML
					A1009101.MXF
					A1009101.SIF
				A10092/
					A10092.CIF
					A10092.CPF
					A10092.XML
					A1009201.MXF
					A1009201.SIF
					A1009202.MXF
					A1009202.SIF
					A1009203.MXF
					A1009203.SIF
					A1009204.MXF
					A1009204.SIF
				INDEX.MIF
				JOURNAL/

Each clip has it’s own folder like (A10091, A10092, etc.).  Video and audio data are stored together in the .MXF files.  Clips longer than about 5 minutes or so will be spanned across multiple .MXF files.  So from the folder structure above you could tell that clip A10091 is less than 5 minutes long and clip A10092 is longer than 15 minutes.

### AMA Linking

To get this in the Avid you want to go to File > Link to AMA Volume... and choose the root card folder.  From the example above it would be the `CARDROOT` folder.

If you’re choosing the right folder and still nothing is importing there are a couple things you can check:

  1. Make sure you have the Canon XF plugin installed.
  2. Make sure your footage was shot at a supported framerate.

To check if you have the plugin installed, in Media Composer, bring up the Console by going to Tools > Console or hit Cmd+6, then enter the command `ama_listplugins`.  If you don’t see a line for `Canon XF`, then you need to install the Canon XF Plugin which you can find on the [Avid Media Access Plug-ins](http://www.avid.com/US/products/Avid-Media-Access/plug-ins) page.

To check the framerate of your footage, use the Canon XF Utility, which you can download from the [Canon EOS C300 - Drivers & Software](http://usa.canon.com/cusa/professional/products/professional_cameras/cinema_eos_cameras/eos_c300#DriversAndSoftware) page.

I’ve personally had success with 1080p/23.976 and 1080i/59.94.  Last time I tried importing 1080p/24.00, AMA would not work.  I’m sure this will change at some point so maybe check in with [this Avid Forums thread](http://community.avid.com/forums/p/113309/655930.aspx) or the [Canon XF AMA Plug-In Guide](http://avid.force.com/pkb/articles/en_US/User_Guide/en367181) for updates.

The solution I used was to rewrap the .MXF files with [Encloader](http://encloader.com/) as Quicktime files (.mov), then ”legacy import” into Media Composer.

### Caveat

If you have any clips that require multiple Canon XF .MXF files (i.e. are longer than 5 minutes or so) *and* were shot at a different framerate than your project, then that footage isn't going to playback without first being rendered.

The solution is to use (in Media Composer) File > Link to AMA File(s), then choose the .MXF files individually.  This may effect the amount of metadata that gets associated with your clips.  I noticed the codec gets recognized as XDCAM instead of Canon XF when I do this, but the picture looks the same and timecodes are consistent which is all I care about.

### Consolidate

After creating AMA clips, I like to Consolidate them.  In Media Composer go to Clip > Consolidate/Transcode.  This will take the Canon XF .MXF files and rewrap them as Avid native .MXF files.  This step isn’t strictly necessary but I’ve had very good editing experiences doing it this way and I can’t say the same for my attempts at pure AMA workflows.
