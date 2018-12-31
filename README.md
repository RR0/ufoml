# ufoml
This project is an attempt to run Machine Learning algorithms on UFO data in order to see what outcomes of interest this could provide.

## Goals
Here are possible goals that could be reached when applying ML to UFO data:

- **Classification as an IFO**: That is, the ability to predict that an UFO case 
will fall in a given category, which could either be "identified/unidentified" 
but more interestingly an identified class ("plane", "reentry", "balloon", 
"star", "hoax", etc.), if any.
- **Categorization of UFOs**, that is, 
identify the several "clusters" of "unidentified' data that share common characteristics. This would help to:
  1. characterize distinct types of unknown phenomenon ; 
  2. find out if some of those types could be assimilated to known phenomena (but failed to be so because of missing/incorrect data typically).

## Input data

Input data comes in two steps:

1. Raw data from outside the system ;
1. That same data, but pre-processed for ML.

### Raw input

Input would come for UFO cases databases available as raw files (.csv typically).

### Preprocessed input

This is a re-engineering of the raw input(s) to avoid duplicates, standardize scales and types, etc.
and more of all select appropriate features (data rows characteristics) to feed during system training.

#### Features

Aside the data size, the characteristics (or "features") of an UFO case are critical to perform a good prediction, so :

- they should be numerous. Typical features could be:
    - date/time
    - location
    - shape
    - color(s)
    - path
    - duration
    - sound
    - apparition/disparition
    - witnesses info (number, profile...)
    - etc.
    
##### IFO Features
If the goal is IFO classification, the supervised learning algorithm will require 
a supplementary indicating the devised classification ("plane", "reentry", "balloon", 
"star", "hoax", etc.) for the IFO case.

##### Media feature
A specific case of feature would be media such as photo, video or audio recordings,
which could be predicted to match a known visual phenomenon (after training the system on a number of strange-but-known photos of natural or mundane phenomena typically)
using some Neural Network.

While this should ideally be a feature among others (in order to not process the image alone but ponderate it with context information),
it might be too complex/performance costly to mix it with other data as a first step.

#### The problem of reliability
As the goal is not to predict cases as being "unidentified" (this would more be a case of "failure to predict"), the reliability of the data comes in two parts:

- **reliability of known IFOs**: As those known IFOs will be the basis for training the system, the reliability of their data is critical. 
That is, the system will only be able to predict what those cases say about reality possibilities. Hopefully IFOs cases are well documented 
and rarely contested, so their reliability is hight.
- **reliability of tested UFOs**: This is the reliability of the data we gathered about a case which has not (yet) be explained ; 
so basically this is the reliability of the investigation on this case.

## Prediction

### The skewed classes problem
The UFO data corpus, if considered as a binary classification ("identified/unidentified") would be a typical case of 
"skewed classes", where one class is typically a lot more common that the other. This could lead to biased precision metrics, 
as in such a case it is easy to seem precise (say 90%) when predicting the case as systematically identified (if supposed roughly 90% as well).

While techniques exist to mitigate that problem (such as the F metric), it could more easily and interestingly avoided 
by targeting multiple identified classes ("plane", "star", "hoax", etc.) that are more evenly distributed among the explanation space.

In such a case where :
- the population of identified is a lot more common than 
unidentified classes
- the characteristics of unidentified/anomalies are unpredictable

it would also be a good idea to use **anomaly detection**
(i.e. 
gaussian probability of an anomaly).

### Explanability
When classifying a case, it would be of particular interest to associate the answer with some explanability so it could be understood/verified by investigators.

## See also

Predictive statistics, Baye