
![python3](https://img.shields.io/badge/Python-3.7-blue)
# pycovid19

### Jupyter notebooks with plots through [plotly](https://plot.ly/python/) library for COVID-19 datasets.

> Data Repository by Johns Hopkins CSSE:   
> https://github.com/CSSEGISandData/COVID-19

---
## Time-series

 - For rendered time-series and forecast go  --> [![colab link](https://camo.githubusercontent.com/52feade06f2fecbf006889a904d221e6a730c194/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/athanoid/pycovid19/blob/master/covid19_reg.ipynb)

[![enter image description here](https://raw.githubusercontent.com/athanoid/pycovid19/master/fig/fig1_1.png)](https://colab.research.google.com/github/athanoid/pycovid19/blob/master/covid19_reg.ipynb)

---
## Map
- For rendered bubble-map go --> [![colab link](https://camo.githubusercontent.com/52feade06f2fecbf006889a904d221e6a730c194/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/github/athanoid/pycovid19/blob/master/covid19_bubblemap.ipynb)

[![enter image description here](https://raw.githubusercontent.com/athanoid/pycovid19/master/fig/fig4_1.png)](https://colab.research.google.com/github/athanoid/pycovid19/blob/master/covid19_bubblemap.ipynb)

## Get report in terminal (linux, mac)

    curl https://my.laseeb.org/~thanos/covid_19/report_gr

## Export to html

    #generate html
    s = str('Date: '+dates[np.size(dates)-1]+ '<br>---')
    s += '<br>Current cases: '+ str(cur) +  (' - Mortality rate: '+ str(mortality_rate) + '%') + '<br>Predicted: ' + str(pred) + '<br>Diff: ' + str(cur-pred)
    s += '<br><br>Next day prediction: '+str(nxt_pred)+  '  - mortality prediction: '+ str(int(np.round(nxm,0))) + ' patients'
    s += '<br><br>Incidents will:<br> - double approximately in ' + str(double_days(x,y,xf,yf)) + ' days' + '<br><br>---'
            
    def figures_to_html(figs, filename="~/Desktop/dashboard_"+country+".html"):
        dashboard = open(filename, 'w')
        dashboard.write("<html><head></head><body>" + "\n")
        dashboard.write("<font face='arial' color='black'>")
        dashboard.write("<div align='center'><h3>"+"COVID19: "+country+"</h3></div> " + "<br>")
        dashboard.write("<meta charset='UTF-8'>")    
        dashboard.write(s + "<br>") #write text
    
        for fig in figs:
            inner_html = fig.to_html().split('<body>')[1].split('</body>')[0]
            dashboard.write(inner_html)
          
        dashboard.write("<div align='center'><a href=\"https://colab.research.google.com/github/athanoid/pycovid19/blob/master/covid19_reg.ipynb\" target=\"_blank\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a></div><br>")    
        
        dashboard.write("</font></body></html>" + "<br>")
            
    figures_to_html([fig1, fig2, fig3, fig4, fig5])

example: https://my.laseeb.org/~thanos/covid_19/dashboard_Greece.html
