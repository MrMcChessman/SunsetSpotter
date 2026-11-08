Try it out
 [sunset-score.vercel.app](sunset-score.vercel.app)

**Inspiration**
Inspiration was two-fold. Earlier this week, I watched a YouTube video titled I discovered a sound that leaks your exact location (Doppler Cracking) and was captivated. In the video, colsto uses publicly available airplane flight path data, and some complex mathematical formulas in order to locate an incredibly obscure video of pixelated treetops. Further down the rabbit hole, he locates the drop location for an anime ending in a sealed chest off the cost of Japan, but this time querying satellites. In the end, he finds the data by narrowing down potential locations, estimating cloud height, and using sunset photos from social media to determine the time and location of the drop.

Second, my family adores sunsets; it's all they send in our shared group chat. Other ideas for what project to choose popped in and out of my head throughout the week, but this sunset one really stuck. I know I will use this tool no matter what, and so will my family. It was nerve-wracking checking to see if the satellites I would need to rely on sampled frequently enough to be useful; and it was a huge relief yesterday morning to find out they did - GOES East.

Data crunching has always fascinated me, and this has been a great challenge to take that passion to the next level.

**What it does**
The user inputs an Address or coordinate location (or selects the button to automatically grab it), and selects the date they'd like the sunset prediction for. The prediction goes up to 10 days out, or selecting dates backwards works up to two days backwards. Additionally, historical datasets are available to give users a better scenario under which to practice.

After user inputs location and date and selects Calculate, the python script begins to run on Vercel. The first packets sent back contain base info, such as the sunset score, and score breakdown. The score is based off the following variables at different weights: whether Sun gets through (or is blocked), whether color is expected, Clouds toward the sunset, and whether they bounce light from the sun, and the amount of sunlight shining in a dome overhead, and onto the sky opposite the viewer (my personal favorite part of sunsets :)

The next packets to come in are for the multi-state top-down view, and the perspective-rendered ground angle. Both first are pushed with the sunset frame, and as the viewer admires the beauty of their forecasted sunset, the remainder of the timeline fills in. Users can scroll at any level of timeline full-ness, it will simply skip to the nearest available frame.

When the user decides to keep the timeline cursor at the sunset, they are granted with even more options. First, the original two views (multi-state top-down and ground-based perspective-rendered) gain six new filters. The first three allow for the user to select from which layer of the atmosphere they would like to see clouds from. For example, selecting "High" will display only cirrus cloud coverage, and other coverage at that elevation. The second filter enabled by Sunset Mode is Data. This view color codes clouds based on elevation rather than sun reflection. Two new views are also available in sunset mode: ground-based upward facing dome, which captures the full sky dome at sunset, and reverse view which captures the view directly opposite the viewer.

**How it was built**
The original method set out in a massive text file I partially dictated, partially typed laid out the general guidelines for the project. From there, continued iteration on the fly was the best ally. Long-winded prompts describing outcomes with meticulous detail, the ability to pivot when efficiency hits snags, and a problem-solving attitude. As a freshman taking CSCI I at RPI, I appreciate taking dirty data and parsing it into clean data, then running an algorithm on that data to output results. That is what the first half of this hackathon was; ensuring the data beneath was rock solid before adding any type of decorative flair or extra features.

**Challenges**
The most notable challenge happened when the result came back that the free API limit had been hit for the first data source that was tried. The free API had a 400 request limit per minute, and a 5000 request daily limit. At least 500 requests were needed for any type of decent dataset construction. The response suggested handicapping the code to wait a minute between each query, and to live with the 10 request per day limit. I found this unacceptable, especially given the free availability of GOES data. What followed was a deep search of the internet, accessing government websites across the internet in search of decent data parsing that didn't rely on the backup, image processing of cloud-cover within Python. Finally, we found "Thredds". Unlimited free queries. A 40 year old website design meant the data was top-notch.

**Accomplishments that we're proud of**
I am happy to have taken part in my first ever hackathon, it is pretty awesome! Turning an idea into something real is something I will never get over, and the ability to leverage advanced tools to hopefully contribute a creative, unique, and useful tool to HackRPI is something I am very proud of!

**What was learned**
From the friends I met at Boba, I not only learned what teacher to take Data Structures with this spring, but also took away a sense of happiness from the amazing community I saw here at HackRPI. Collaboration, goofiness, and an overall welcoming and acceptive vibe are something I truly appreciate. If I learned anything, it is that leveraging tools to create a project I am passionate about while remaining totally engaged and incorporating guidance, corrections, and creative solutions along the way is a satisfying way to spend a weekend.

**What's next for Sunset Spotter**
I might even add a Sunrise mode! I hope my family appreciates this tool. Another benefit of hosting on a server like Vercel means I can send a link to my family so they can appreciate and play with the tool as well.

If I'm ever bored between classes or on a weekend, I think this is definitely a project I would pick back up and play around with again. There is so much more I can implement, and am excited to see how I can use the skills I learn at RPI to improve this project along the way!

Built With
claude
python
vercel
Try it out
 [sunset-score.vercel.app](sunset-score.vercel.app)
