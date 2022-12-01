## Reasons to Fake Data

There's an emerging market of solutions for helping you generate fake date and anonymize existing data.  Historically this is an area where many data scientists built home grown solutions.  As these practices have become more commonplace, practitioneers are looking to libraries and tools that can help them with fake data.  But what's the use of fake data in the first place?  In my persional experience, there have been three key reasons:

### Limiting the Blast Radius

Even when you and all your employees follow perfect IT security processes, we are all vunerable to zero day exploits.  Whether you manage data on behalf of your organization or a client, no one wants to be the source of a data breech.  One of the best ways to be secure is to have nothing worth stealing.  I can even say I've one a few contracts in part because I'm able to operate in a way where I can deliver results to clients without ever touching their data directly.

A major enabling innovation is docker.  My deliverable is a git repository containing a Dockerfile that any qualified DevOps engineer (with a little help from the README) could build and deploy on whatever architecture or cloud they use.  That container typically exposes a REST API and a basic administrative web interface.  In many cases, I have no access to client data but I can do things like use the API to trigger a machine learning training job or inspect the resulting model via the web.  In more sensitive cases, I might not even get that access.

Developing a solution that involves machine learning invarible calls for some amount of exploratory data analysis and feature engineering.  Consider credit card fraud detection.  The raw data contains information like the merchant's metadata, transaction amount, time of day, etc.  An incredibly useful bit of information to have when trying to detect fraud is whether or not the customer has used their card with that exact merchant in the past for similar amounts and with similar frequency?  The answer can be encoded as a single binary digit, but calculation of this feature can be a non-trivial task to engineer.

Many ML practitioners will be quick to complain: how can I build useful features if I can't see the real data?  This concern is not without merit.  Where possible, production-like fake data should meet their needs more than adaquetly.  For high sensitivity cases when an organization is hesitant to provide even anonymized data, you've got to fake it completely from scratch.


### Protecting Private Date

In bygone eras of technology, companies would frequently make a snapshot of a production database and provide this to developers to assist in their work.  It's true that a software engineer's output will be better when building applications with realistic data context.  Providing an empty database and a few poorly mocked manual test cases leaves great opportunities for gaps in design that won't appear until after a release.  Yet, today it is literally criminal to haphazardously move personal information around that way.

Developers don't need true production data.  They can more than get by on production-like data.  A simple fix in many cases is to encrypt all personal data as a salted hash of the original.  That does the job, but it leaves developers looking at random strings instead of typical fields like name and email.  This opens the door for CSS errors and puts a mental tax on developers that might otherwise benefit from testing their work on realistic, more memorable data.

More sophisticated techniques now exist to statistically anonymize datasets while holding true to many of the underlying distributions of the data.  For example, generating a set of mock customers whose city, state, and age distributions match the true dataset is entirely possible.  I can't imagine doing serious development on a web app without a tool that is privacy protecting yet statistically faithful.


### Last Mile Machine Learning

In any machine learning project, there's a plot with time on the x-axis and some metric (often accuracy) on the y-axis.  The accuracy usually begins just a bit above random chance, and as the engineer improves their features, adjusts their architecture, explores hyperparameters, or changes the loss function, the accuracy will monotonically increase over time.

Early gains on this journey yield quick improvements.  Invariably, all problems reach some scaling limit.  For some, improving the accuracy demands new features which might be costly to implement and maintain.  For others, the limited datset of the small or medium size business is all that's available and thus limiting the opportunity for ML.  When the total population is not enough, fake data is the only option.

One weakness that many ML models have is data sparsity.  If there are areas of the input space for which it has few previous examples, the model's output will often be rather unpredicable.  This makes the model vunerable to adversarial attacks.  Consider again the case of credit card fraud detection.  It's a cat and mouse game.  It's possible for an ML team to stay ahead by anticipating new potential attacks or suspecious behavior and teaching their model how to spot pro-actively identified fraud pathways.

Fraud is also a classic example of the classic problem of class imbalance.  Despite the serious expense and potential for damage to a business, the vast majority of their transactions are not fraud.  A phoney model which labels all transactions as "no fraud" is likely to be correct at least 99% of the time, while simultaneously being utterly useless.  If your problem has a class imbalance, fake data is one of the techniques you should be trying.

## In Conclusion

A mature machine learning team that isn't actively using a fake data solution should at least be having casual lunch discussions about it.  The sensitivity of the data you work on will often be the motivating factor for adoption.  But beyond that, there's a number of good reasons for fake data to be a part of your ML pipeline, especially as that pipeline matures.






