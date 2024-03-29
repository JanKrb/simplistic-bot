![test](logo_long.png)

#

## About
Simplistic wude im Rahmen der Projekttage der TBS1 entwickelt. Simplistic besteht aus zwei Teilen. In diesem Repo wird nur der Discord-Bot angesprochen. Dieser Discord-Bot besitzt Funktionen für die Verwaltung von klasseninternen Daten wie Hausaufgaben und Klassenarbeiten. Die Verwaltung dieser Daten ist meist eine Errinerung an die Hausaufgaben oder die anstehende Klassenarbeit. Doch Simplistic bietet mehr als nur Funktionen für Klassen. Der Bot bietet verschiedene Module für verschiedene Zwecke.

## Das Team
+ Marvin G.
  + War für die allgemeine Botstruktur verantworlich sowie das erstellen von sämtlichen Modulen.

+ Mirco L.
  + War für die Datenbank zuständig sowie das erstellen des Schul-/Profilmoduls.

+ Justin S.
  + Bearbeitete hauptsächlich die Simplistic-App (siehe anderes Repo).

+ Kevin D.
  + Bearbeitete genauso wie Justin die App (siehe anderes Repo).

## Alle verfügbaren Module
|Modul   |Beschreibung   |
|---|---|
|Cases   |Dieses Modul basiert auf den Funktionen von Lootboxen. User können für die Botwährung Kisten öffnen um Booster zu erhalten.   | 
|Gambling   |Hier können User einige Minispiele spielen um das eigene Vermögen zu vermehren.   |
|Economy   |Beinhaltet alles was mit der Botwährung zutun hat.   |
|Fun   |Das Modul ist dafür da um z.B. Memes in einem Channel zu senden.   |
|Moderation   |Dieses Modul hilft den Moderatoren die Community sauber zu halten.   |
|Profil   |Hier befinden sich alle Profil relevanten Funktionen.   |
|School   |Mit diesem Modul kann eine Klasse z.B. die Hausaufgaben festhalten und bekommen automatisch eine erinerrung.   |
|Drone   |Dieses Modul stellt ein Cockpit zur verfügung um eine ARDrone zu fliegen.   |

## Was sind Module?
Module sind extra angelegte .py Dateien die einen bestimmten Themenbereich abdecken wie z.B. das Economy-Modul. Die Module ansich heißen aber "cogs". Die Module werden automatisch über das eigentliche Bot-Skript in den Bot eingebunden. So ein Modul kann dann während der Bot läuft bearbeitet werden und neugeladen werden ohne den Bot neu zu starten.

## Erstellen von Modulen
Um ein komplett eigenes Modul zu erstellen kann man diese Vorlage verwenden.
```
import discord
import sys
from discord.ext import commands
import os
import platform

def getpath():
    config_path = None
    if platform.system() == "Windows":
        config_path = os.path.dirname(os.path.dirname(os.path.abspath(__file__))) + "\\scripts\\"
    if platform.system() == "Linux":
        config_path = os.path.dirname(os.path.dirname(os.path.abspath(__file__))) + "/scripts"
    return config_path

sys.path.insert(1, getpath())
import database as db
import embed_builder as eb

class TestModul(commands.Cog):
    def __init__(self, bot):
        self.bot = bot

    @commands.Cog.listener()
    async def on_ready(self):
        print("Test module loaded.")

    @commands.command()
    async def ping(self, ctx):
        await ctx.send("Pong!")
   
def setup(bot):
    bot.add_cog(TestModul(bot))
```
