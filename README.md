MediaBrowser.Kodi.SkinHelper
============================

Skin helper functions/services for Kodi MediaBrowser AddOn

XBMC add-on name: script.mediabrowser.skinhelper 

add-on service/script for skins that utilize the MediaBrowser add-on for Kodi

By using this service you no longer have to utilize the xbmb3c addon with the skin command!

Please REMOVE this line from your skin if you only want to use the new window properties:
<onload condition="System.HasAddon(plugin.video.plexbmc)">RunScript(plugin.video.xbmb3c,skin)</onload>

Note: if you keep the skin initialize intact you will also have the old xbmb3c. window properties


The service provides the following window properties:

## USER COLLECTIONS
MediaBrowser.usr.X.title  --> title of collection
MediaBrowser.usr.X.path  --> path to collection (defaults to collapsed boxsets for movies)
MediaBrowser.usr.X.type  --> the type of the collection
MediaBrowser.usr.X.total  --> total items in the collection
MediaBrowser.usr.X.fanart --> fanart image of the collection as serverside
MediaBrowser.usr.X.background --> random rotating fanart image of the collection as serverside
MediaBrowser.usr.X.background.small --> random rotating fanart (smaller) image of the collection as serverside
MediaBrowser.usr.X.recent.path --> link to recently added items of the collection
MediaBrowser.usr.X.recent.content --> link to recently added contentpath for use in widgets
MediaBrowser.usr.X.unwatched.path --> link to unwatched items of a collection
MediaBrowser.usr.X.unwatched.content --> link to unwatched contentpath for use in widgets
MediaBrowser.usr.X.inprogress.path --> link to in-progress items of a collection
MediaBrowser.usr.X.inprogress.content --> link to in-progress contentpath for use in widgets
MediaBrowser.usr.X.genre.path --> link to genres of a collection
MediaBrowser.usr.X.nextepisodes.path --> link to next episodes of a tvshow-collection
MediaBrowser.usr.X.nextepisodes.content --> link to next episodes contentpath for use in widgets

## STANDARD ITEMS
MediaBrowser.std.movies.0 - All Movies  --> will default to collapsed boxsets
MediaBrowser.std.movies.1 - Recently Added Movies
MediaBrowser.std.movies.2 - In Progress Movies
MediaBrowser.std.movies.3 - Favorite Movies
MediaBrowser.std.movies.4 - BoxSets
MediaBrowser.std.movies.5 - Unwatched Movies
MediaBrowser.std.movies.6 - Movie Genres
MediaBrowser.std.movies.7 - Movie Studios
MediaBrowser.std.movies.8 - Movie Actors

MediaBrowser.std.tvshows.0 - All TV
MediaBrowser.std.tvshows.1 - Recently Added Episodes
MediaBrowser.std.tvshows.2 - In Progress Episodes
MediaBrowser.std.tvshows.3 - Next Episodes
MediaBrowser.std.tvshows.4 - Favorite Shows
MediaBrowser.std.tvshows.5 - Favorite Episodes
MediaBrowser.std.tvshows.6 - Upcoming TV
MediaBrowser.std.tvshows.7 - Unwatched Episodes
MediaBrowser.std.tvshows.8 - TV Genres
MediaBrowser.std.tvshows.9 - TV Networks
MediaBrowser.std.tvshows.10 - TV Actors

MediaBrowser.std.music.0 - All Music
MediaBrowser.std.music.1 - Recently Added Albums
MediaBrowser.std.music.2 - Frequent Played Albums
MediaBrowser.std.music.3 - Music Videos
MediaBrowser.std.music.4 - Songs
MediaBrowser.std.music.5 - Albums
MediaBrowser.std.music.6 - Album Artists
MediaBrowser.std.music.7 - Artists
MediaBrowser.std.music.8 - Genres

MediaBrowser.std.photo.0 - Photos

MediaBrowser.std.channels.0 - Channels

MediaBrowser.std.playlists.0 - Playlists

MediaBrowser.std.search.0 - Search



## Extra rotating random background images provided by the service
These come additional to the existing random background images

MB3.Background.FavouriteMovies.FanArt  --> random fanart image of user's favourite movies
MB3.Background.FavouriteMovies.FanArt.small  --> random fanart image of user's favourite movies (smaller version for use in widgets etc)
MB3.Background.FavouriteShows.FanArt --> random fanart image of user's favourite tvshows
MB3.Background.FavouriteShows.FanArt.small
MB3.Background.Channels.FanArt  --> random fanart images of channels available in the MB3 server
MB3.Background.Channels.FanArt.small
MB3.Background.MusicVideos.FanArt --> random fanart of available musicvideos on the MB3 server
MB3.Background.MusicVideos.FanArt.small 
MB3.Background.Photos.FanArt --> random picture on the mb3 server
MB3.Background.Photos.FanArt.small


--> The background images rotate every 60 seconds


## Functions available in the script for skinners

# Set forced view for contenttype in addon
Skinners can use the script to store the view in the XBMB3C settings.
Usage: Add the following code to the "change view" button in MyVideoNav -->

<onclick condition="substring(Container.FolderPath,plugin://plugin.video.xbmb3c) + Container.Content(Movies)">XBMC.RunScript(service.mediabrowser.skinhelper,SETVIEW,MOVIES,00)</onclick>
<onclick condition="substring(Container.FolderPath,plugin://plugin.video.xbmb3c) + Container.Content(seasons)">XBMC.RunScript(service.mediabrowser.skinhelper,SETVIEW,SEASONS,00)</onclick>
<onclick condition="substring(Container.FolderPath,plugin://plugin.video.xbmb3c) + Container.Content(TVShows)">XBMC.RunScript(service.mediabrowser.skinhelper,SETVIEW,SERIES,00)</onclick>
<onclick condition="substring(Container.FolderPath,plugin://plugin.video.xbmb3c) + Container.Content(Episodes)">XBMC.RunScript(service.mediabrowser.skinhelper,SETVIEW,EPISODES,00)</onclick>
<onclick condition="substring(Container.FolderPath,plugin://plugin.video.xbmb3c) + Container.Content(Sets)">XBMC.RunScript(service.mediabrowser.skinhelper,SETVIEW,BOXSETS,00)</onclick>

Please notice that the '00' indicates that the script will automatically locate the view from the skin's views.xml file
Skinners may choose to replace the 00 manually with the viewnumber to set the view


# set default settings for the XBMB3C addon compatible with the skin

XBMC.RunScript(service.mediabrowser.skinhelper,SETRECOMMENDEDMB3SETTINGS,SKINNAME)

replace SKINNAME with the name of the skin (has to be added to the code of the service)
--> Now only used for Titan and 1080XF skins


