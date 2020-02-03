# DimuonSpectrum2010

This is a simple analysis example to compute the spectrum of two muon final state with CMS Open Data.

It is based on the [Example code](http://opendata.web.cern.ch/record/560) to produce the di-muon spectrum from a CMS 2010 primary dataset on the CERN Open Data portal (Geiser, Achim. Dutta, Irene. Hirvonsalo, Harri. Sheeran, Bridget. (2017). CERN Open Data Portal. DOI: 10.7483/OPENDATA.CMS.B8MR.C4A2) and another github project [DimuonSpectrum2011](https://github.com/cms-opendata-analyses/DimuonSpectrum2011), and modified here for direct download from github. 

The modifications with respect to the original code are the following: 

- the class name has been changed from `DemoAnalyzer` to `DimuonSpectrum2010` in order to avoid conflict for any existing `DemoAnalyzer` plugins in the working area
- the file paths have been modified to be relative in the configuration file, i.e. they point to the `datasets` directory, which is under the directory from where there program will be run.

Run this code in [CMS Open Data VM](http://opendata.web.cern.ch/VM/CMS/2010)

If you have not installed the CMSSW area do the following:

```
cmsrel CMSSW_4_2_8
```

You can also run this code on the [CMS Open Data Docker Image](http://opendata.cern.ch/docs/cms-guide-docker) if you are interested in that.

If you already have the CMSSW or run the docker container, start directly with:

```
cd CMSSW_4_2_8/src
cmsenv
```

For this example, you need to create an additional directory, you can call it `WorkDir` or choose another name.
Go to this directory, and download the example code.

```
mkdir WorkDir
cd WorkDir
git clone git://github.com/PhyM73/DimuonSpectrum2010.git

```

Go to the example directory, and compile with `scram b`. 

```
cd DimuonSpectrum2010
scram b
```

The input files are defined in the configuration file `demoanalyzer_cfg.py` and are already in the `datasets` directory. This example runs on 2010 data by default. In order not to overwrite the existing DoubleMu.root, to which you can compare your output, rename it before you run.

Run the example as configured in the configuration file. 

```
cmsRun demoanalyzer_cfg.py
```

The output of the example is a root file containing several histograms, by default DoubleMu.root with 10000 input events (small subset of data). These can be looked at using a Root Browser.

For more detailed information, read the comments in src/DimuonSpectrum2010.cc.
