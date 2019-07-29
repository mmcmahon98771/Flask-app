# Flask-app
Flask
import requests

api_url = 'https://api.bls.gov/publicAPI/v2/timeseries/data/' % earnings
session = requests.Session()
session.mount('http://', requests.adapters.HTTPAdapter(max_retries=3))
raw_data = session.get(api_url)

from bokeh.plotting import figure

plot = figure(tools=TOOLS,
              title='Data from BLS',
              x_axis_label='date',
              x_axis_type='datetime')
              
              from bokeh.embed import components 

script, div = components(plot)
return render_template('graph.html', script=script, div=div)


<html>
  <head>
    <link rel="stylesheet" href="http://cdn.pydata.org/bokeh/release/bokeh-0.12.0.min.css" type="text/css" />
    <script type="text/javascript" src="http://cdn.pydata.org/bokeh/release/bokeh-0.12.0.min.js"></script>
    {{ script | safe }}
  </head>
  <body>
    <div class=page>
      <h1>Header text</h1>
      {{ div | safe }}
    </div>
  </body>
</html>
