# tweetoria

In circumstances when other profiling tools may be unavailable, this project explores using recent developments in applying language analysis to social media sources in an attempt to determine basic user characteristics. It is constructed primarily with the goal of performing market research and customer profiling on a specific topic, person or brand, as represented by querying a term or terms via the Twitter [Streaming](https://dev.twitter.com/streaming/overview) and [REST](https://dev.twitter.com/rest/overview) APIs.

This is an ELK-based ([elasticsearch](https://www.elastic.co/products/elasticsearch), [logstash](https://www.elastic.co/products/logstash) & [kibana](https://www.elastic.co/products/kibana)) tool configured to ingest, filter, & format streaming data from Twitter or similar feeds, index and store, tokenize content, execute lexical analysis, and visually represent results on a rolling basis.

**Possible subsets of users:**
- follow a given account
- *interact* (@ mention, reply) with a given account
- talk *about* (but not with) a given account


### Caveats
Care must be taken to consider bias inherent to the source data. Most obvious is that results represent *only* the portion of the general population that
- has access to the internet,
- uses Twitter,
- is discussing the search term, and 
- is active during the period of the sample. 

Search terms themselves may also be subject to inherent bias, and any resultant analysis should be carefully considered with this in mind.

### Roadmap
- [Tokenize](https://www.elastic.co/guide/en/elasticsearch/reference/current/analysis-tokenizers.html) Determine if the required tokenization for chosen lexica may be effectively implemented within the ELK workflow.
- [Filters](https://www.elastic.co/guide/en/elasticsearch/reference/current/analysis-tokenfilters.html)
- [Lexical Analysis]() TBD
- [Alerts](https://www.elastic.co/products/watcher) Sudden changes in results may trigger notifications.
- _Geocoding_ [Photon](https://github.com/komoot/photon) Either in the same ES instance or allocated geocoder instance, implement Photon & attempt to generate point data based on `user.location` field. *Note: this is the location the user lists in their Twitter profile, not the coordinates of the tweet itself.*

### Other applications
- Depending on the lexicon applied and related validation factors, a similar assessment could be applied to text compiled from other publicly-available sources, such as comments in issues and pull requests associated with open source software development, user forums or discussion modules, and messaging applications such as Slack or Hipchat.

### Working References, Sources & Influences
- [Discovering User Attribute Stylistic Differences via Paraphrasing](http://wwbp.org/papers/discovering_user_attribute.pdf), 2016
 - [Data](https://figshare.com/articles/Paraphrase_choice_based_on_user_traits/1613525)
- [Developing age and gender predictive lexica over social media](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=gFN4QUYAAAAJ&citation_for_view=gFN4QUYAAAAJ:9yKSN-GCB0IC), 2014 
- [Characterizing geographic variation in well-being using tweets.](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=Na16PsUAAAAJ&citation_for_view=Na16PsUAAAAJ:d1gkVwhDpl0C)
- [Analyzing Personality through Social Media Profile Picture Choice](http://wwbp.org/papers/persimages16icwsm.pdf), 2016
- [Studying user income through language, behaviour and affect in social media](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0138717), 2015
 - [Data](https://figshare.com/articles/Twitter_User_Income_Dataset/1515997)
- [Analyzing crowdsourced assessment of user traits through Twitter posts](https://sites.sas.upenn.edu/danielpr/publications/analyzing-crowdsourced-assessment-user-traits-through-twitter-posts)
- [An analysis of the user occupational class through Twitter content](http://wwbp.org/papers/jobs15acl.pdf), 2015


### Resources & Libraries
- [langid.py tool](https://github.com/saffsd/langid.py) (Lui and Baldwin 2012) Standalone language identification system
- [Faces++](https://github.com/FacePlusPlus/facepp-python-sdk/tree/v2.0) Cloud-based Facial recognition API (free)
- [EmoVu](http://emovu.com/e/developers/api/) Deep Learning-based emotion recognition (50 free/month, then $195/mo)
- [Natural Language Processing with Python](http://www.nltk.org/book/)
