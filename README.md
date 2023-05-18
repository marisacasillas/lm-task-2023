# technical task for lab manager applicants (2023)


This repository contains instructions for two short tasks to complete by **DEADLINE**. These tasks were chosen because they are representative samples of the kinds of things our lab manager does.

I'm hoping that this will take 1–3 hours of your time in total, depending on how experienced you are with these kinds of tasks and how determined you are to double check your work and/or add extra bells and whistles.

The purpose of these tasks is for me to get a sense of where your strengths are when it comes to data-centered tasks. Equally important, these tasks should also give you a glimpse into the kinds of data-centered tasks that our lab manager leads.

Each task is described below. For each there is a "satisfaction" goal and a "reach" goal. It's perfectly fine to set your aims on the satisfaction goal!

**Please share your work by creating a GitHub repository and adding me as a collaborator (@marisacasillas).** I strongly advise you to use the repository throughout your work time, rather than working offline and then only uploading the final version to GitHub.

If you have any questions along the way, please reach out. Thank you!!

## task 1: timecode conversion

### background

For several of our tasks, members of our lab may need to switch between timecodes expressed in different formats. For example, 6 hours, 13 minutes, and 10 seconds could be expressed as 061310 (HHMMSS), as 06:13:10 (HH:MM:SS), 06h13m10s (HHhMMmSSs), as 373.1667 minutes, as 22390 seconds, etc.

It's uesful to have a quick way to convert between formats because some of our softwares use different formats from each other (e.g., Praat uses seconds and ELAN uses HH:MM:SS.MS) and because sometimes we want to use a single software's timecodes in a kind of clunky way (e.g., computing the difference in time between two HH:MM:SS.MS times).

### instructions

Please write an R script that can compute the conversion between two timecodes: HH:MM:SS.MS and seconds. So, for example, the script would contain a function that takes as input `06:13:10.459` and gives as output `22390.459` *OR* that takes as input `22390.459` and gives as output `06:13:10.459`.

Imagine that the person using this script is an undergraduate RA who has extremely limited experience/comfort with R.

#### satisfaction goal: R script, hard-coded paths

A satisfaction solution is a single/set of R scripts and a README for which:

* I can run the code to load your function(s)
* I can identify the name of your conversion function(s) and how to use them (commented code is useful!)
* I can call your function(s) and give it/them, as an argument, a time in one of the two format types to get the desired output, e.g., `convert_time_chatter(06:13:10.459)` should give `22390.459`
* The given outputs are correct (rounded to three digits in the case of milliseconds)

_Why this goal level?_ Students and RAs in the lab who are just learning how to script are likely doing so in R, particularly in RStudio. Even if they're just beginning, they will probably know (or can be taught) how to open, minorly edit, and run individual scripts, and so would probably be able to use a tool like this independently after a little initial instruction.

#### reach goal

A reach solution is a Shiny app for which:

* I can visit the webpage to load your code
* I can identify where and how to enter the input time in order to ask the webpage for a conversion (e.g., by entering `06:13:10.459` or `22390.459`)
* The given outputs are correct

If you haven't encountered a [Shiny app](https://www.shinyapps.io/) before, here's an example: [https://aclew.shinyapps.io/schober\_clark\_replication/](https://aclew.shinyapps.io/schober_clark_replication/). This webpage allows users to upload an ELAN file and then it checks the file for a variety of different error types and reports the results of the check to the uploader. Underlyingly, it is run by a set of R scripts that we keep [here](https://github.com/marisacasillas/chatterlab/tree/gh-pages/content/courses/HLI2022/schober_clark_replication) (the primary .eaf checker code is in `check-eaf.R` and the webpage interface code is in `app.R`). If you do this solution I recommend developing the code in RStudio, which makes it easy to set up the connection to Shiny. If you don't already have one, you can sign up for a free Shiny account [here](https://www.shinyapps.io/auth/oauth/signup).

_Why this level?_ Everyone can use this tool, no matter their experience with programming, which makes it incredibly useful.

## task 2: transcription

### background

We are currently embarking on two projects that will involve large quantities of audio/video transcription (e.g., [this one](https://neubauercollegium.uchicago.edu/research/roots-of-linguistic-identity) and [this one](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2238609&HistoricalAwards=false)). We have a long training process with very specific conventions for things like what to transcribe and what to ignore, how to use contractions like "wanna", how to indicate things like laughter and crying, and so on. But that's WAY too much for your current task. Right now I would only like to get a preliminary impression of how you would use ELAN to generate a simple transcript.

While we have existing workflows for setting up transcription documents and completing transcription, an important part of the lab manager's job is experimenting with and then documenting best ways to adapt those workflows for new projects. For example, you might take the instructions and training materials from the [ACLEW project](https://osf.io/b2jep/wiki/home/) and create a minimal version for a student to use on a specific pilot dataset they will work on. So imagine this as a moment when you're experimenting with a best way to do transcription for a new project.

For the purposes of this task, I want to you imagine that we're going to create transcripts such that they are maximally and flexibly re-usable for child language research. For example, you can imagine that the resulting transcripts + media files might be used to study any aspect of linguistic input or child vocalization that could be extracted from orthographic transcription and/or the timestamps associated with the accurate onset and offset of vocalizations. This is a very free-form task, there's really no right answer!

### instructions

#### initial preparation

* Download [this daylong audio file](https://media.talkbank.org/homebank/Public/FauseyTrio-Public/G448/G448_001100.wav) from HomeBank.
  * (!) Please note that there is more than one child in this recording, and also in the clips I will highlight below.
* Create a new ELAN file and attach the daylong audio as linked media.
* Rename the default tier as `coded_region` and create two annotations on that tier, each 30 seconds long, starting at:
  * `06:58:30.349` 
  * `07:10:00.000`
* Add values to those annotations of `technical_task_1` and `technical_task_2`, respectively
* Save your ELAN file with a sensible name

#### satisfaction goal: transcription only

A satisfaction solution is an ELAN file that has, minimally, one tier for each speaker featured in the highlighted clips (see above). All hearable speech should be be transribed. Some tips:

* Use conventional US English spellings
* Sometimes it's unclear whether an utterance should be lumped together over a silence or, instead, split into multiple pieces. Whatever you do, do it systematically
* Feel free to use an indicator for unintelligible speech, either at the word level or at the whole utterance level
* Make your onset and offset boundaries reasonably accurate:
  * When I play each of your utterance annotations individually, I shouldn't hear silence preceding/following the transcribed speech for that annotation
  * When I play each of your utterance annotations there shouldn't be cut off parts of the transcribed speech at the start or end 
* Nonlinguistic infant vocalizations can be transcribed as "0." (the period there is part of the transcription)
* It's up to you whether you want to transcribe other nonlinguistic, yet communicative behaviors, such as laughter
* Feel free to add further tiers as desired (e.g., comments, addressee, etc.)
* Generally, high systematicity is valued over high detail, but transcriptions with _both_ features are ideal


#### reach goal: transcription + proposed coding scheme

A reach solution is the ELAN file above, accompanied by a README file (e.g., .md > .doc, but both are acceptable) that documents your systematic approach to transcription. You would, for example, create this document _after_ you have experimented a little and decided on a best approach to transcription. Its purpose is to guide an imagined undergraduate research assistant on how to use your transcription strategy with new audio clips. You want them to be able to replicate what you would do, as closely as possible. So imagine that this person would read your document and then start to transcribe other clips from other recordings just on the basis of what you have written. What would you write to get them to closely produce what you would have yourself produced? Some tips:

* Use concrete examples whenever relevant
* It's typically useful to try and anticipate common errors/misunderstandings
* It's good to provide supplemental resources (e.g., screen shots/animated gifs/audio clips/dictionary links/other documents/start-up instructions) as needed

This is a very freeform task. I'll mostly be looking at what you find interesting/how you engage with it and how clear your document is for a typical RA in our lab.

