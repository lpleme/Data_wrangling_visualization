---
title: "DT"
author: "YOUR NAME"
date: "March 10, 2020"
output:
  html_document:  
    keep_md: true
    toc: true
    toc_float: true
    code_folding: hide
    fig_height: 6
    fig_width: 12
    fig_align: 'center'
---






```r
# Use this R-Chunk to import all your datasets!
```

## Background

_Place Task Background Here_

## Data Wrangling


```r
# Use this R-Chunk to clean & wrangle your data!
datatable(head(iris), colnames = c('ID' = 1), options = list(pageLength = 5, dom = 'tip'), rownames = FALSE)
```

<!--html_preserve--><div id="htmlwidget-c18854e334bb97e212fa" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-c18854e334bb97e212fa">{"x":{"filter":"none","data":[[5.1,4.9,4.7,4.6,5,5.4],[3.5,3,3.2,3.1,3.6,3.9],[1.4,1.4,1.3,1.5,1.4,1.7],[0.2,0.2,0.2,0.2,0.2,0.4],["setosa","setosa","setosa","setosa","setosa","setosa"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th>ID<\/th>\n      <th>Sepal.Width<\/th>\n      <th>Petal.Length<\/th>\n      <th>Petal.Width<\/th>\n      <th>Species<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"dom":"tip","columnDefs":[{"className":"dt-right","targets":[0,1,2,3]}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

## Data Visualization


```r
# Use this R-Chunk to plot & visualize your data!
library(dygraphs)
lungDeaths <- cbind(mdeaths, fdeaths)
dygraph(lungDeaths) %>% 
  dyRangeSelector()
```

<!--html_preserve--><div id="htmlwidget-e46138f82f72a2999e41" style="width:1152px;height:576px;" class="dygraphs html-widget"></div>
<script type="application/json" data-for="htmlwidget-e46138f82f72a2999e41">{"x":{"attrs":{"labels":["month","mdeaths","fdeaths"],"legend":"auto","retainDateWindow":false,"axes":{"x":{"pixelsPerLabel":60}},"showRangeSelector":true,"rangeSelectorHeight":40,"rangeSelectorPlotFillColor":" #A7B1C4","rangeSelectorPlotStrokeColor":"#808FAB","interactionModel":"Dygraph.Interaction.defaultModel"},"scale":"monthly","annotations":[],"shadings":[],"events":[],"format":"date","data":[["1974-01-01T00:00:00.000Z","1974-02-01T00:00:00.000Z","1974-03-01T00:00:00.000Z","1974-04-01T00:00:00.000Z","1974-05-01T00:00:00.000Z","1974-06-01T00:00:00.000Z","1974-07-01T00:00:00.000Z","1974-08-01T00:00:00.000Z","1974-09-01T00:00:00.000Z","1974-10-01T00:00:00.000Z","1974-11-01T00:00:00.000Z","1974-12-01T00:00:00.000Z","1975-01-01T00:00:00.000Z","1975-02-01T00:00:00.000Z","1975-03-01T00:00:00.000Z","1975-04-01T00:00:00.000Z","1975-05-01T00:00:00.000Z","1975-06-01T00:00:00.000Z","1975-07-01T00:00:00.000Z","1975-08-01T00:00:00.000Z","1975-09-01T00:00:00.000Z","1975-10-01T00:00:00.000Z","1975-11-01T00:00:00.000Z","1975-12-01T00:00:00.000Z","1976-01-01T00:00:00.000Z","1976-02-01T00:00:00.000Z","1976-03-01T00:00:00.000Z","1976-04-01T00:00:00.000Z","1976-05-01T00:00:00.000Z","1976-06-01T00:00:00.000Z","1976-07-01T00:00:00.000Z","1976-08-01T00:00:00.000Z","1976-09-01T00:00:00.000Z","1976-10-01T00:00:00.000Z","1976-11-01T00:00:00.000Z","1976-12-01T00:00:00.000Z","1977-01-01T00:00:00.000Z","1977-02-01T00:00:00.000Z","1977-03-01T00:00:00.000Z","1977-04-01T00:00:00.000Z","1977-05-01T00:00:00.000Z","1977-06-01T00:00:00.000Z","1977-07-01T00:00:00.000Z","1977-08-01T00:00:00.000Z","1977-09-01T00:00:00.000Z","1977-10-01T00:00:00.000Z","1977-11-01T00:00:00.000Z","1977-12-01T00:00:00.000Z","1978-01-01T00:00:00.000Z","1978-02-01T00:00:00.000Z","1978-03-01T00:00:00.000Z","1978-04-01T00:00:00.000Z","1978-05-01T00:00:00.000Z","1978-06-01T00:00:00.000Z","1978-07-01T00:00:00.000Z","1978-08-01T00:00:00.000Z","1978-09-01T00:00:00.000Z","1978-10-01T00:00:00.000Z","1978-11-01T00:00:00.000Z","1978-12-01T00:00:00.000Z","1979-01-01T00:00:00.000Z","1979-02-01T00:00:00.000Z","1979-03-01T00:00:00.000Z","1979-04-01T00:00:00.000Z","1979-05-01T00:00:00.000Z","1979-06-01T00:00:00.000Z","1979-07-01T00:00:00.000Z","1979-08-01T00:00:00.000Z","1979-09-01T00:00:00.000Z","1979-10-01T00:00:00.000Z","1979-11-01T00:00:00.000Z","1979-12-01T00:00:00.000Z"],[2134,1863,1877,1877,1492,1249,1280,1131,1209,1492,1621,1846,2103,2137,2153,1833,1403,1288,1186,1133,1053,1347,1545,2066,2020,2750,2283,1479,1189,1160,1113,970,999,1208,1467,2059,2240,1634,1722,1801,1246,1162,1087,1013,959,1179,1229,1655,2019,2284,1942,1423,1340,1187,1098,1004,970,1140,1110,1812,2263,1820,1846,1531,1215,1075,1056,975,940,1081,1294,1341],[901,689,827,677,522,406,441,393,387,582,578,666,830,752,785,664,467,438,421,412,343,440,531,771,767,1141,896,532,447,420,376,330,357,445,546,764,862,660,663,643,502,392,411,348,387,385,411,638,796,853,737,546,530,446,431,362,387,430,425,679,821,785,727,612,478,429,405,379,393,411,487,574]]},"evals":["attrs.interactionModel"],"jsHooks":[]}</script><!--/html_preserve-->


```r
dygraph(lungDeaths) %>%
  dySeries("mdeaths", label = "Male") %>%
  dySeries("fdeaths", label = "Female") %>%
  dyOptions(stackedGraph = TRUE) %>%
  dyRangeSelector(height = 20)
```

<!--html_preserve--><div id="htmlwidget-430df6dc49c2c7054b3a" style="width:1152px;height:576px;" class="dygraphs html-widget"></div>
<script type="application/json" data-for="htmlwidget-430df6dc49c2c7054b3a">{"x":{"attrs":{"labels":["month","Male","Female"],"legend":"auto","retainDateWindow":false,"axes":{"x":{"pixelsPerLabel":60,"drawAxis":true},"y":{"drawAxis":true}},"series":{"Male":{"axis":"y"},"Female":{"axis":"y"}},"stackedGraph":true,"fillGraph":false,"fillAlpha":0.15,"stepPlot":false,"drawPoints":false,"pointSize":1,"drawGapEdgePoints":false,"connectSeparatedPoints":false,"strokeWidth":1,"strokeBorderColor":"white","colorValue":0.5,"colorSaturation":1,"includeZero":false,"drawAxesAtZero":false,"logscale":false,"axisTickSize":3,"axisLineColor":"black","axisLineWidth":0.3,"axisLabelColor":"black","axisLabelFontSize":14,"axisLabelWidth":60,"drawGrid":true,"gridLineWidth":0.3,"rightGap":5,"digitsAfterDecimal":2,"labelsKMB":false,"labelsKMG2":false,"labelsUTC":false,"maxNumberWidth":6,"animatedZooms":false,"mobileDisableYTouch":true,"disableZoom":false,"showRangeSelector":true,"rangeSelectorHeight":20,"rangeSelectorPlotFillColor":" #A7B1C4","rangeSelectorPlotStrokeColor":"#808FAB","interactionModel":"Dygraph.Interaction.defaultModel"},"scale":"monthly","annotations":[],"shadings":[],"events":[],"format":"date","data":[["1974-01-01T00:00:00.000Z","1974-02-01T00:00:00.000Z","1974-03-01T00:00:00.000Z","1974-04-01T00:00:00.000Z","1974-05-01T00:00:00.000Z","1974-06-01T00:00:00.000Z","1974-07-01T00:00:00.000Z","1974-08-01T00:00:00.000Z","1974-09-01T00:00:00.000Z","1974-10-01T00:00:00.000Z","1974-11-01T00:00:00.000Z","1974-12-01T00:00:00.000Z","1975-01-01T00:00:00.000Z","1975-02-01T00:00:00.000Z","1975-03-01T00:00:00.000Z","1975-04-01T00:00:00.000Z","1975-05-01T00:00:00.000Z","1975-06-01T00:00:00.000Z","1975-07-01T00:00:00.000Z","1975-08-01T00:00:00.000Z","1975-09-01T00:00:00.000Z","1975-10-01T00:00:00.000Z","1975-11-01T00:00:00.000Z","1975-12-01T00:00:00.000Z","1976-01-01T00:00:00.000Z","1976-02-01T00:00:00.000Z","1976-03-01T00:00:00.000Z","1976-04-01T00:00:00.000Z","1976-05-01T00:00:00.000Z","1976-06-01T00:00:00.000Z","1976-07-01T00:00:00.000Z","1976-08-01T00:00:00.000Z","1976-09-01T00:00:00.000Z","1976-10-01T00:00:00.000Z","1976-11-01T00:00:00.000Z","1976-12-01T00:00:00.000Z","1977-01-01T00:00:00.000Z","1977-02-01T00:00:00.000Z","1977-03-01T00:00:00.000Z","1977-04-01T00:00:00.000Z","1977-05-01T00:00:00.000Z","1977-06-01T00:00:00.000Z","1977-07-01T00:00:00.000Z","1977-08-01T00:00:00.000Z","1977-09-01T00:00:00.000Z","1977-10-01T00:00:00.000Z","1977-11-01T00:00:00.000Z","1977-12-01T00:00:00.000Z","1978-01-01T00:00:00.000Z","1978-02-01T00:00:00.000Z","1978-03-01T00:00:00.000Z","1978-04-01T00:00:00.000Z","1978-05-01T00:00:00.000Z","1978-06-01T00:00:00.000Z","1978-07-01T00:00:00.000Z","1978-08-01T00:00:00.000Z","1978-09-01T00:00:00.000Z","1978-10-01T00:00:00.000Z","1978-11-01T00:00:00.000Z","1978-12-01T00:00:00.000Z","1979-01-01T00:00:00.000Z","1979-02-01T00:00:00.000Z","1979-03-01T00:00:00.000Z","1979-04-01T00:00:00.000Z","1979-05-01T00:00:00.000Z","1979-06-01T00:00:00.000Z","1979-07-01T00:00:00.000Z","1979-08-01T00:00:00.000Z","1979-09-01T00:00:00.000Z","1979-10-01T00:00:00.000Z","1979-11-01T00:00:00.000Z","1979-12-01T00:00:00.000Z"],[2134,1863,1877,1877,1492,1249,1280,1131,1209,1492,1621,1846,2103,2137,2153,1833,1403,1288,1186,1133,1053,1347,1545,2066,2020,2750,2283,1479,1189,1160,1113,970,999,1208,1467,2059,2240,1634,1722,1801,1246,1162,1087,1013,959,1179,1229,1655,2019,2284,1942,1423,1340,1187,1098,1004,970,1140,1110,1812,2263,1820,1846,1531,1215,1075,1056,975,940,1081,1294,1341],[901,689,827,677,522,406,441,393,387,582,578,666,830,752,785,664,467,438,421,412,343,440,531,771,767,1141,896,532,447,420,376,330,357,445,546,764,862,660,663,643,502,392,411,348,387,385,411,638,796,853,737,546,530,446,431,362,387,430,425,679,821,785,727,612,478,429,405,379,393,411,487,574]],"fixedtz":false,"tzone":""},"evals":["attrs.interactionModel"],"jsHooks":[]}</script><!--/html_preserve-->


```r
hw <- HoltWinters(ldeaths)
predicted <- predict(hw, n.ahead = 72, prediction.interval = TRUE)

dygraph(predicted, main = "Predicted Lung Deaths (UK)") %>%
  dyAxis("x", drawGrid = FALSE) %>%
  dySeries(c("lwr", "fit", "upr"), label = "Deaths") %>%
  dyOptions(colors = RColorBrewer::brewer.pal(3, "Set1"))
```

<!--html_preserve--><div id="htmlwidget-20deebab1e92c3c445ad" style="width:1152px;height:576px;" class="dygraphs html-widget"></div>
<script type="application/json" data-for="htmlwidget-20deebab1e92c3c445ad">{"x":{"attrs":{"axes":{"x":{"pixelsPerLabel":60,"drawGrid":false,"drawAxis":true},"y":{"drawAxis":true}},"title":"Predicted Lung Deaths (UK)","labels":["month","Deaths"],"legend":"auto","retainDateWindow":false,"customBars":true,"series":{"Deaths":{"axis":"y"}},"stackedGraph":false,"fillGraph":false,"fillAlpha":0.15,"stepPlot":false,"drawPoints":false,"pointSize":1,"drawGapEdgePoints":false,"connectSeparatedPoints":false,"strokeWidth":1,"strokeBorderColor":"white","colors":["#E41A1C","#377EB8","#4DAF4A"],"colorValue":0.5,"colorSaturation":1,"includeZero":false,"drawAxesAtZero":false,"logscale":false,"axisTickSize":3,"axisLineColor":"black","axisLineWidth":0.3,"axisLabelColor":"black","axisLabelFontSize":14,"axisLabelWidth":60,"drawGrid":true,"gridLineWidth":0.3,"rightGap":5,"digitsAfterDecimal":2,"labelsKMB":false,"labelsKMG2":false,"labelsUTC":false,"maxNumberWidth":6,"animatedZooms":false,"mobileDisableYTouch":true,"disableZoom":false},"scale":"monthly","annotations":[],"shadings":[],"events":[],"format":"date","data":[["1980-01-01T00:00:00.000Z","1980-02-01T00:00:00.000Z","1980-03-01T00:00:00.000Z","1980-04-01T00:00:00.000Z","1980-05-01T00:00:00.000Z","1980-06-01T00:00:00.000Z","1980-07-01T00:00:00.000Z","1980-08-01T00:00:00.000Z","1980-09-01T00:00:00.000Z","1980-10-01T00:00:00.000Z","1980-11-01T00:00:00.000Z","1980-12-01T00:00:00.000Z","1981-01-01T00:00:00.000Z","1981-02-01T00:00:00.000Z","1981-03-01T00:00:00.000Z","1981-04-01T00:00:00.000Z","1981-05-01T00:00:00.000Z","1981-06-01T00:00:00.000Z","1981-07-01T00:00:00.000Z","1981-08-01T00:00:00.000Z","1981-09-01T00:00:00.000Z","1981-10-01T00:00:00.000Z","1981-11-01T00:00:00.000Z","1981-12-01T00:00:00.000Z","1982-01-01T00:00:00.000Z","1982-02-01T00:00:00.000Z","1982-03-01T00:00:00.000Z","1982-04-01T00:00:00.000Z","1982-05-01T00:00:00.000Z","1982-06-01T00:00:00.000Z","1982-07-01T00:00:00.000Z","1982-08-01T00:00:00.000Z","1982-09-01T00:00:00.000Z","1982-10-01T00:00:00.000Z","1982-11-01T00:00:00.000Z","1982-12-01T00:00:00.000Z","1983-01-01T00:00:00.000Z","1983-02-01T00:00:00.000Z","1983-03-01T00:00:00.000Z","1983-04-01T00:00:00.000Z","1983-05-01T00:00:00.000Z","1983-06-01T00:00:00.000Z","1983-07-01T00:00:00.000Z","1983-08-01T00:00:00.000Z","1983-09-01T00:00:00.000Z","1983-10-01T00:00:00.000Z","1983-11-01T00:00:00.000Z","1983-12-01T00:00:00.000Z","1984-01-01T00:00:00.000Z","1984-02-01T00:00:00.000Z","1984-03-01T00:00:00.000Z","1984-04-01T00:00:00.000Z","1984-05-01T00:00:00.000Z","1984-06-01T00:00:00.000Z","1984-07-01T00:00:00.000Z","1984-08-01T00:00:00.000Z","1984-09-01T00:00:00.000Z","1984-10-01T00:00:00.000Z","1984-11-01T00:00:00.000Z","1984-12-01T00:00:00.000Z","1985-01-01T00:00:00.000Z","1985-02-01T00:00:00.000Z","1985-03-01T00:00:00.000Z","1985-04-01T00:00:00.000Z","1985-05-01T00:00:00.000Z","1985-06-01T00:00:00.000Z","1985-07-01T00:00:00.000Z","1985-08-01T00:00:00.000Z","1985-09-01T00:00:00.000Z","1985-10-01T00:00:00.000Z","1985-11-01T00:00:00.000Z","1985-12-01T00:00:00.000Z"],[[2147.20785194564,2645.16348198456,3143.11911202347],[2110.18139788162,2608.15247676059,3106.12355563957],[2045.14373555805,2543.14213650641,3041.14053745477],[1572.71148495348,2070.75244140209,2568.7933978507],[1033.62152908981,1531.72363230797,2029.82573552614],[867.998993899734,1366.18418949325,1864.36938508678],[818.023017563286,1316.3166006104,1814.61018365752],[638.120541413507,1136.55115001774,1634.98175862198],[649.462691946833,1148.06229898902,1646.6619060312],[1015.70094238838,1514.50484526417,2013.30874813997],[1167.92739514489,1666.97420327936,2166.02101141382],[1618.44545921371,2117.77707915073,2617.10869908775],[2046.7057053279,2551.1923693382,3055.6790333485],[2009.31987361748,2514.18136411423,3019.04285461098],[1943.88351293492,2449.17102386005,2954.45853478518],[1471.01342203736,1976.78132875573,2482.54923547409],[931.44668929247,1437.75251966162,1944.05835003076],[765.30867474868,1272.2130768469,1779.11747894511],[714.778781570045,1222.34548796404,1729.91219435804],[534.284248921203,1042.58003737139,1550.87582582157],[544.996535823456,1054.09118634266,1563.18583686186],[910.567484417037,1420.53373261782,1930.49998081859],[1062.08960394722,1573.003090633,2083.91657731877],[1511.86674952771,2023.80596650437,2535.74518348103],[1937.86426994651,2457.22125669184,2976.57824343717],[1899.67667286665,2420.21025146787,2940.7438300691],[1833.40403679274,2355.19991121369,2876.99578563464],[1359.6637614848,1882.81021610937,2405.95667073394],[819.193577673878,1343.78140701526,1868.36923635664],[652.119529158701,1178.24196420054,1704.36439924237],[600.621744020496,1128.37437531768,1656.12700661487],[419.128227036753,948.608924725027,1478.0896224133],[428.811242812123,960.1200736963,1491.42890458048],[793.323478061043,1326.56261997146,1859.80176188187],[943.758324361609,1479.03197798664,2014.30563161167],[1392.42055543843,1929.83485385801,2467.24915227759],[1816.05594808444,2363.25014404548,2910.44434000652],[1776.71892713733,2326.23913882152,2875.75935050571],[1709.27243525616,2261.22879856733,2813.18516187851],[1234.33488443909,1788.83910346301,2343.34332248693],[692.645042610108,1249.8102943689,1806.97554612769],[524.330013137201,1084.27085155418,1644.21168997116],[471.571003320954,1034.40326267133,1597.2355220217],[288.797113954592,854.637812078668,1420.47851020274],[297.181719495127,866.148961049942,1435.11620260476],[660.378627302809,1232.5915073251,1804.80438734739],[809.48235729176,1385.06086534028,1960.6393733888],[1256.79881607332,1835.86374121165,2414.92866634999],[1678.20945727424,2269.27903139912,2860.348605524],[1637.5210913904,2232.26802617516,2827.01496095991],[1568.71180792749,2167.25768592097,2765.80356391446],[1092.40110765323,1694.86799081665,2297.33487398008],[549.328837916314,1155.83918172254,1762.34952552877],[379.623169404808,990.299738907821,1600.97630841083],[325.466361978336,940.432150024968,1555.3979380716],[141.288551691705,760.66669943231,1380.04484717292],[148.264128564559,772.177848403584,1396.09156824261],[510.047893567476,1138.62039467874,1767.19289579],[657.735336178666,1291.08975269392,1924.44416920918],[1103.63330660219,1741.8926285653,2380.1519505284],[1523.12392491016,2175.30791875276,2827.49191259537],[1481.03243961756,2138.2969135288,2795.56138744004],[1410.81998558302,2073.28657327462,2735.75316096621],[933.106878079423,1600.89687817029,2268.68687826117],[388.633748146405,1061.86806907618,1735.10239000596],[217.529518462934,896.328626261463,1575.12773405999],[161.977168464692,846.461037378609,1530.94490629253],[-23.5924791797967,666.695586785951,1356.9836527517],[-18.0043811845254,678.206735757225,1374.41785269898],[342.396883111522,1044.64928203238,1746.90168095324],[488.70738922196,1197.11864004756,1905.52989087317],[933.234539793752,1647.92151591894,2362.60849204412]]],"fixedtz":false,"tzone":""},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

## Conclusions


