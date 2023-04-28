# Lyon-Deberge-Deniaud
Krikorian Mathis &amp; Deniaud Lucas

import pandas as pd

# Importer le fichier CSV des précipitations et créer un DataFrame pandas
df = pd.read_csv("precipitations.csv", delimiter=",")

print(df)


import folium 
from folium.plugins import HeatMap


# Créer une carte centrée sur les coordonnées moyennes de tous les emplacements
m = folium.Map(location=[df['LAT'].mean(), df['LON'].mean()], zoom_start=8)

# Ajouter une couche de carte de chaleur à la carte pour montrer les précipitations
heat_data = [[row['LAT'], row['LON'], row['ANN']] for index, row in df.iterrows()]
HeatMap(heat_data).add_to(m)

# Afficher la carte
# Enregistrer la carte dans un fichier HTML
m.save("carte_heatmap.html")
