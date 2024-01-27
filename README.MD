# INSTALATION
## INSTALL conda enviroment and packages (one time)

>conda create -n shazam python=3.9  
>conda activate shazam  
>pip install -r requirements.txt

## Shazam Algorithm in a Nutshell
1. Sliding Window (Divide to Conquer)
> Each song is divided into multiple segments/windows, with some overlap between them (e.g. segments of seconds)  
2. Fourier Analysis  
> From time domain to frequency domain. The frequency spectrum is more robust to noise and therefore it is prefered  
3. Obtaining the most prominant peaks as representations
> For each segment/window, the most prominent peaks are obtained (e.g. around 15 for each segment). The prominence of 
a peak measures how much a peak stands out from the surrounding baseline of the signal and is defined as the vertical 
distance between the peak and its lowest contour line.  
4. Combinatorial Hashing
> The most important (prominent) peaks are not enough, since different song may share the same range of frequencies. A more robust representation considers the difference between consecutive peaks as representation. For each prominent peak, many representations (hashes) are obtained considering another peak further in time and its relative time difference.
5. Finding Matches (Time difference)
> Even with Combinatorial Hashing many hash collisions are shared among different songs. To tackle this issue, one should consider the offset of these matches. For a given sample (let's say 15 seconds of a song) and a music database, we should not only compare the hash collisions but also the time difference between them. If several collisions between the sample and a song in the database have the same offset (time diference), then we probably found our match. 
