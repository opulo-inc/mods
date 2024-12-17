---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# <span class="badge badge-primary">Github</span><span class="badge badge-secondary">Github</span><span class="badge badge-success">Github</span><span class="badge badge-danger">Github</span><span class="badge badge-info">Github</span>

title: "OpenPnP Mods"
layout: single
header:
  overlay_color: "#000"
  overlay_filter: "0.65"
  overlay_image: /assets/img/feature.jpg
  caption: "Photo credit: **Tobias Netzer**"
sidebar:
  nav: "openpnp"
---

## Four step fiducial pipeline

**Made by:** LixieLabs

**Description**: An alternative to OpenPNP’s default fiducial vision pipeline. It uses DetectCircularSymmetry to obtain more consistent results. Copy the code below and use the “paste” icon in OpenPNP’s vision settings panel to use it. This pipeline also works for nozzle tip calibration.

```xml
<cv-pipeline>
   <stages>
      <cv-stage class="org.openpnp.vision.pipeline.stages.ImageCapture" name="image" enabled="true" default-light="true" settle-first="true" count="1"/>
      <cv-stage class="org.openpnp.vision.pipeline.stages.MaskCircle" name="mask" enabled="true" diameter="500" property-name="MaskCircle"/>
      <cv-stage class="org.openpnp.vision.pipeline.stages.DetectCircularSymmetry" name="cir" enabled="true" min-diameter="10" max-diameter="150" max-distance="250" search-width="0" search-height="0" max-target-count="1" min-symmetry="1.2" corr-symmetry="0.0" property-name="" outer-margin="0.2" inner-margin="0.4" sub-sampling="8" super-sampling="1" diagnostics="false" heat-map="true"/>
      <cv-stage class="org.openpnp.vision.pipeline.stages.ConvertModelToKeyPoints" name="results" enabled="true" model-stage-name="cir"/>
   </stages>
</cv-pipeline>
```

## Linux camera configuration script

**Made by**: Atanisoft / Curly Tale Games

**Link to source**: [https://gist.github.com/atanisoft/41abe04de117978ba74710b8955d845e](https://gist.github.com/atanisoft/41abe04de117978ba74710b8955d845e)

**Description**: Curly Tale Games created the original script for automatic reconfiguration of cameras on Linux during startup of OpenPnP, however, it was a mix of shell script and Python code. This version is strictly Python code.

This script is no longer necessary if you are using the latest version of Open PnP

## KiCad OpenPnP import script

**Made by:** Atanisoft

**Link to source**: [https://github.com/atanisoft/FeederUtils/tree/main/kicad_tools](https://github.com/atanisoft/FeederUtils/tree/main/kicad_tools)

**Description**: Automation script for importing KiCad PCBs directly into OpenPnP, including package and part details.