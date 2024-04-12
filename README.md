<h1>SQL Journey Through Music Analytics</h1>

 ### [Medium Article Demonstration](https://medium.com/@sebastienwebdev/sql-journey-through-music-analytics-363f5e3bc98b)

<h2>Description</h2>
This project delves into the vast datasets of Spotify using SQL to uncover patterns and insights within the music industry. Utilizing the "Spotify Dataset 1921–2020, 160k+ Tracks" from Kaggle, we explore various metrics like acousticness, danceability, and more. Our analysis aims to understand music taste evolution, identify success factors for tracks, and analyze artist diversity across genres..
<br />

<h2>Environments & Utilies Used </h2>

- <b>macOS</b> 
- <b>SQLite Studio</b>
- <b>Database (Kaggle) </b>


<h2>Program walk-through:</h2>

<h2>What are the top 10 most popular songs?</h2>
    <pre><code>SELECT name, artists, popularity 
FROM spotify_data 
ORDER BY popularity DESC 
LIMIT 10;</code></pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*tQOte-dXV1zSzgQrJeeZpA.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />
<h2>Which artists have the highest number of tracks in the dataset?</h2>
    <pre><code>SELECT artists, COUNT(*) as track_count 
FROM spotify_data 
GROUP BY artists 
ORDER BY track_count DESC 
LIMIT 10;</code></pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*S8HCSMW1f_h8oJNeJsQ1Vg.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />
    <h2>What is the average loudness of the top 50 most popular songs?</h2>
    <pre><code>SELECT AVG(loudness) as average_loudness 
FROM (SELECT loudness FROM spotify_data ORDER BY popularity DESC LIMIT 50);
</code></pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*BB8Up9yfvrWoWDXvH1Crag.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />
    <h2>How many explicit tracks are there in each year?</h2>
    <pre><code>SELECT year, COUNT(*) as explicit_count 
FROM spotify_data 
WHERE explicit = 1 
GROUP BY year;</code>
</pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*f4xIXUtbG-Zng6qrtE9S5g.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />
    <h2>What are the average values of danceability, energy, and valence for the most popular songs?</h2>
    <pre><code>SELECT AVG(danceability) as avg_danceability, AVG(energy) as avg_energy, AVG(valence) as avg_valence 
FROM spotify_data 
WHERE popularity > 80;</code></pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*ZwhmzTs8YPA3lvu9ZEFNNA.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />
    <h2>Which key is the most common among all tracks?</h2>
   

<pre><code>SELECT key, COUNT(*) as key_frequency FROM spotify_data 
GROUP BY key 
ORDER BY key_frequency DESC 
LIMIT 1;
</code></pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*p8VEO7aSDjhTxWBjx9bOFA.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />
    <h2>Are there any correlations between the song’s popularity and its acoustic characteristics like ‘acousticness’ or ‘instrumentalness’?</h2> 
    <pre><code>SELECT 
  popularity, 
  AVG(acousticness) as avg_acousticness, 
  AVG(instrumentalness) as avg_instrumentalness 
FROM spotify_data 
GROUP BY popularity;</code></pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*aJhUsyE6Gk8usHtCwXBqSQ.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />
    <h2>What is the duration range (shortest and longest track) for songs with high danceability scores?</h2>
    <pre><code>SELECT 
  MIN(duration_ms) as min_duration, 
  MAX(duration_ms) as max_duration 
FROM spotify_data 
WHERE danceability > 0.8;</code></pre>
<img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*PDxtHthHeKc6ZBHKnOGa5Q.png" height="80%" width="80%" alt="music Steps"/>
<br />
<br />

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
