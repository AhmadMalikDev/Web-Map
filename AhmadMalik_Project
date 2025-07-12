import folium
import pandas
from branca.element import Element
from folium.plugins import MiniMap
from folium.plugins import Fullscreen
fscreen =Fullscreen()
minimap = MiniMap()
data = pandas.read_csv("project.csv")
long = list(data["Longitude"])
lat = list(data["Latitude"])
names = list(str(data["Name"]))

html = """<div style="width:220px; font-family: Arial">
            <h4 style="color:#1a5f1a; margin-bottom:5px">Place Information</h4>
            <hr style="margin:5px 0">
            <b>Name:</b> %s<br>
          </div>"""

map = folium.Map(location=[31.5497, 74.3436],zoon_start=12,tiles = "OpenStreetMap")


fg = folium.FeatureGroup(name="My Maps")
for l1,l2,l3 in zip(lat,long,data["Name"]):
    iframe = folium.IFrame(html=html % str(l3), height=100, width=200)
    display =folium.Popup(iframe,max_width=200)
    fg.add_child(folium.Marker(location=[l1, l2],popup= display, icon=folium.Icon(color = "green",icon = "star",prefix = "fa")))

header_html = """
<div style="position: fixed;
            top: 10px;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(135deg, #1a5f1a, #3aab3a);
            border: 2px solid #0d3b0d;
            color: white;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.5);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 12px 25px;
            border-radius: 10px;
            font-size: 24px;
            font-weight: bold;
            z-index: 9999;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;">
        Chronicles in Stone | By Ahmad Malik
</div>
"""
map.get_root().html.add_child(Element("""
<style>
    #map {
        border: 5px solid #af4261;
        box-shadow: 0 0 20px rgba(0,0,0,0.3);
    }
</style>
"""))

map.get_root().html.add_child(Element(header_html))
map.add_child(fg)
       
map.add_child(minimap)   
map.add_child(fscreen)

map.save("Python_Project.html")
#print(map)
print("Python Project saved")
