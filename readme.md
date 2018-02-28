# same site different day

A website where people watch a user submitted playlist of youtube videos

## Theoretical operation
- user loads page
- client gets playlist from server
- client renders playlist to the view
- client works out which video to play
- client works out elapsed time by taking the submission time off the present
time
- client takes the video id and elapsed time and requests the video at that time
stamp
- client renders video
- video plays
- client works out when video will end
- client works out which video to play next
- client waits till the video ends and loads next video

- user submits an entry to the playlist
- client takes the entry and checks if it is a valid url
- if it isn't the client returns a message to the user
- if it is the client sends it to the server with the time of submission
- the server adds it to the database
- the server returns that something has changed on its database
- the client goes through getting the playlist again and rendering it


## Design Principles:
- Videos cant be skipped paused or scrubbed
- Everyone sees the same playlist
- Videos are always added to the end of the playlist
- Only single videos can be submitted not playlists


```
View                                                          Database
                                                               +---------------------------------+
+-----------------------------------+                          |            Playlist             |
|    +------------------------+     |                          |   +-------------------------+   |
|    |                        |     |                          |   |                         |   |
|    |       Video            | <----------------+             |   |                         |   |
|    |                        |     |            |             |   |                         |   |
|    +------------------------+     |            +-----------------+ Video ID (URL) - String |   |
|    +------------------------+     |                          |   |  Order in list - Number |   |
|    |                        |     |                          |   |         Played - Boolean|   |
|    |      Submission Form   +----------------------------------> |   Time started - number |   |
|    |                        |     |                          |   |    (and added)          |   |
|    |                        |     |                          |   |         Length - Number |   |
|    +------------------------+     |                          |   | Title of video - String |   |
|    +------------------------+     |                          |   |                         |   |
|    |       Playlist         |     |                          |   |                         |   |
|    |                        | <----------------------------------+                         |   |
|    |                        |     |                          |   |                         |   |
|    +------------------------+     |                          |   |                         |   |
+-----------------------------------+                          |   +-------------------------+   |
                                                               +---------------------------------+
```
