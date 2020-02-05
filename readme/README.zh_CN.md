# DimuonSpectrum2010

本项目是一个使用 CMS Open Data 计算双μ子不变质量谱的简单分析样例。

本项目基于 CERN Open Data 门户网站上的 [Example code to produce the di-muon spectrum](http://opendata.web.cern.ch/record/560) from [a CMS 2010 primary dataset](http://opendata.web.cern.ch/record/14)(Geiser, Achim. Dutta, Irene. Hirvonsalo, Harri. Sheeran, Bridget. (2017). CERN Open Data Portal. DOI: 10.7483/OPENDATA.CMS.B8MR.C4A2) 并将所需文件做了打包，以便直接下载运行。同时，本项目还参考了另一个 GitHub 项目 [DimuonSpectrum2011](https://github.com/cms-opendata-analyses/DimuonSpectrum2011).

对原始代码的修改如下：

- 为了避免与工作区中任何现有的 `DemoAnalyzer` 插件冲突，将类名从 `DemoAnalyzer` 更改为`DimuonSpectrum2010`.
- 文件路径已被修改为相对于配置文件中的相对路径，即它们指向 `datasets` 目录，该目录位于将要运行程序的目录下。

您可以在 [CMS Open Data VM](http://opendata.web.cern.ch/VM/CMS/2010) 上运行此代码。如果您尚未安装 CMSSW，请执行以下操作：

```
cmsrel CMSSW_4_2_8
```

您也可以在 [CMS Open Data Docker](http://opendata.cern.ch/docs/cms-guide-docker) 的容器上运行此代码。如执行以下操作：

```bash
docker run --name dimu2010 -it cmsopendata/cmssw_4_2_8 bash
```

如果您已经安装了 CMSSW 或运行了 Docker 容器，请直接运行如下命令：

```bash
cd CMSSW_4_2_8/src
cmsenv
```

接下来，您需要创建一个工作目录，可以将其命名为 `WorkDir` 或任意其他名称。并将本项目下载到此目录下。

```bash
mkdir WorkDir
cd WorkDir
git clone git://github.com/PhyM73/DimuonSpectrum2010.git

```

再转到本项目的目录，使用 `scram b` 进行编译。

```bash
cd DimuonSpectrum2010
scram b
```

其中输入文件已经在配置文件 ` demoanalyzer_cfg.py` 中定义，并且放置在 `datasets` 目录下。接下来直接运行配置文件即可。

```bash
cmsRun demoanalyzer_cfg.py
```

其输出是一个包含多个直方图的 ROOT 文件，默认情况下命名为 DoubleMu.root, 包含有10000个输入 `event`。您可以使用 ROOT 查看这些内容。您还可以修改 `demoanalyzer_cfg.py` 中的相关部分以选择 `datasets` 中其他的输入文件，并重新运行和比较。或者使用 ROOT 软件将各个输出文件融合起来以获得更全面的分析样本，同时也请注意调节 `demoanalyzer_cfg.py` 中的 `process.maxEvent` 参数。现有的 DoubleMu2010.root 文件可以提供参考。

有关更多详细信息，请参阅 `src/DimuonSpectrum2010.cc` 中的注释。

