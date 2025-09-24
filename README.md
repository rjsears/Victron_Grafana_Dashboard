
<h2 align="center">
  <a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/dashboard.png"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/dashboard.png" alt="Grafana_Dashboard"></a>
  <br>
  Dashboard (V1.0.1 - September 24th, 2025)
  </h2>
  <h4 align="center">Be sure to  :star:  my repo so you can keep up to date on any updates and progress!</h4>
<br>
<div align="center">
    <a href="https://github.com/rjsears/Victron_Grafana_Dashboard/commits/master"><img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/rjsears/Victron_Grafana_Dashboard?style=plastic"></a>
    <a href="https://github.com/rjsears/Victron_Grafana_Dashboard/issues"><img alt="GitHub issues" src="https://img.shields.io/github/issues/rjsears/Victron_Grafana_Dashboard?style=plastic"></a>
    <a href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/master/LICENSE"><img alt="License" src="https://img.shields.io/github/license/rjsears/Victron_Grafana_Dashboard?style=plastic"></a>
 <img alt="GitHub release (latest by date)" src="https://img.shields.io/github/v/release/rjsears/Victron_Grafana_Dashboard?style=plastic">
<img alt="GitHub contributors" src="https://img.shields.io/github/contributors/rjsears/Victron_Grafana_Dashboard?style=plastic">
</h4>
</div><br><br>
  <p align="center">
Simple Grafana Dashboard for monitoring a Solar install
  </p>
<hr>
<b></em><a name="overview"></a>Overview & Theory of Operation</b>
<br><p>
I have some friends who purchased a piece of property that is entirely off-grid. The house was being powered by 4 small panels, an old (but still functional) Xantrex inverter and a couple of small golf cart batteries.  Every night, they would deplete the batteries and lose power. So they purchased a new system, and I helped them install it. 
</p><br>

The system they chose for their needs ended up with the following configuration:
<ul>
  <li><a href="https://www.victronenergy.com/inverters-chargers/multiplus-ii">Victron Multiplus-II 48/5000/120</a></li>
  <li><a href="https://www.victronenergy.com/inverters-chargers/multiplus-ii">Victron MPPT 450/100</li>
  <li><a href="https://www.victronenergy.com/dc-distribution-systems/lynx-distributor">Victron Lynx Distributor</li>
  <li><a href="https://www.victronenergy.com/dc-distribution-systems/lynx-power-in">Victron Lynx Power In</li>
  <li><a href="https://www.victronenergy.com/communication-centres/cerbo-gx">Victron Cergo GX</li>
  <li><a href="https://www.victronenergy.com/display-and-panels/gx-touch-50">Victron GX Touch 70</li>
  <li><a href="https://eg4electronics.com/categories/batteries/eg4-wallmount-indoor-280ah-lithium-battery/">EG4 280Ah LiFePO4 14.3kWh Battery</li>
  <li><a href="https://silfabsolar.com/our-solar-panels/silfab-prime/sil-440-qd/">Ten Silfab Prime 440 Watt Solar Panels</li>
  <li><a href="https://www.generac.com/residential-products/standby-generators/gaseous/14kw-standby-generator-wifi-enabled-7223/">Generac Guardian 14kW Standby Generator</li>
</ul>

<br><hr><br>
Installation and configuration were pretty straightforward. Victron is top-notch hardware, and everything went together and was programmed, and up and running in a single day, not counting the install time for the panels, generator, propane tank, and running all of the necessary wires.
<br><br>
The Cerbo GX ties everything together, and that is where the Touch 70 screen connects, so you can monitor your system.<br>
  
  <p align="center">
<a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/cerbo_gx.png"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/cerbo_gx.png" alt="Grafana_Dashboard" height="700" width="550"></a></p>
<br>
They even offer an online view of the system via a secure website, but while nice, it lacks a lot of in-depth historical data.<br><br>
  <p align="center">
<a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/vrm1.png"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/vrm1.png" alt="Grafana_Dashboard" height="700" width="550"></a></p>
<br>
  <p align="center">
<a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/vrm2.png"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/vrm2.png" alt="Grafana_Dashboard" height="700" width="550"></a></p>
<hr>
Having spent many years using Grafana and InfluxDB for various power and weather projects, I set out to design a dashboard that would provide my friends with more data and allow them to store it for as long as they like for historical reference. The Victron VRM solution only stores data for six months, or so I was told. Besides having absolutly top-notch hardware, Victron also open-sources their software so you can run it on a Pi or whatever. <br><br>When I started looking at how I could get the data myself from the Cerbo GX, imagine my surprise to find out that Victron had already done all the legwork for me! All I needed to do was fire up a VM, grab a simple docker command, and in minutes I was completely up and running with the bare bones of what I needed:
<br><br>
<p align="center">
<a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/vm.png"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/vm.png" alt="Grafana_Dashboard"></a></p>
<br><br>
I'm not going to go into details on how to install all the software since they do an excellent job of it themselves, but I am thankful that they have put this all together for us. Once it was up and running, the only thing left was to create my dashboards!
<br><br>
<a href="https://github.com/victronenergy/venus-grafana">Victron Grafana Repo</a>
<br><br>
So far, I have built two different dashboards, the one shown above, for viewing on a computer, and one laid out just a bit differently for viewing on an iPad. I am using Canvus to automate my generator icon. If you are running your own version of Grafana and Influx and don't want to use the Victron Docker method, make sure your version of Grafana supports Canvus.

<a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/gen_stopped.png"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/gen_stopped.png" alt="Generator Stopped" height="50%" width="50%"></a>
<a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/Generator_running.gif"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/Generator_running.gif" alt="Generator Running"></a>
<hr>
<p align="center">
  <a name="dash" href="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/ipad.png"><img src="https://github.com/rjsears/Victron_Grafana_Dashboard/blob/main/images/ipad.png" alt="Grafana_Dashboard" height="700" width="550"></a></p>
  <br><br>

  I hope this gives people some ideas of what they can do with Grafana and the Victron ecosystem! Enjoy.
  <br><br>
# <a name="changelog"></a>Changelog
<b>V1.0.0 2025-09-20</b>
   - Initial Release

<b>V1.0.1 2025-09-24</b>
   - Added Solar output via Solcast (https://www.solcast/com) free API
   - Added Sun elevation via Sun and Moon Grafana Plugin found <a href="https://grafana.com/grafana/plugins/fetzerch-sunandmoon-datasource/">HERE</a>
   - Added weather banner via <a href="https://weatherwidget.io/">Weatherwidget.io</a> 

