# Predicting Crime in a Big Data World

*Yearly, the world is inundated with news about government data collection programs. In addition to these programs, governments collect data from third party sources to gather information about individuals. This data in conjunction with machine learning aids governments in determining where crime will be committed and who has committed a crime. Could this data serve as a method by which governments predict whether or not the individual will commit a crime? This talk will examine the use of big data in the context of predictive policing. Specifically, how does the data collected inform suspicion about a particular individual? In the context of U.S. law, can big data alone establish reasonable suspicion or should it just factor into the totality of the circumstances? How do we mitigate the biases that might exist in large data sets?*

Whitney Merrill

- https://events.ccc.de/congress/2015/Fahrplan/events/7457.html
- https://media.ccc.de/v/32c3-7457-predicting_crime_in_a_big_data_world


## Talk notes

- Imagine a world.
  - A police officer walks down the street.
  - Has a camera and an ear plug.
  - Gets stats on a possible upcoming crime.
  - Sees a person who fits the possible crime.
  - Should the person be arrested? Searched? Questioned?
  - Do other factors weigh in?
- Using algorithms sometimes said "to have no bias" towards gender, ethincity etcetera.
- Current software.
  - Collect data from many sources.
    - Weather.
    - Geodata.
    - Previous crimes.
  - Targets areas rather than individuals.
  - Data.
    - Split data into training set, validation set, test set.
    - Develop classification rules by analyzing training set.
    - ...
  - Only probabilistic predictions, not suspiscion of individuals.
  - Future plus past.
- Data used.
  - Types.
    - Personal charactersistics (age, gender, race, religion).
    - Decmographic (address, salary, occupation).
    - Activities of indiciduals.
    - Scientific data (radioation data).
  - Sources.
    - Foreign travel info.
    - Video cameras.
    - Biometrics.
    - ...
    - ...
- Hitachi Visualization Predicitve Crima Analytics (PCA).
  - Geoviz.
  - Real-time soecial media and internet data feeds.
- HunchLab.
  - ...
- Domain Awareness Systems (NYC plus Microsoft).
  - Can track indiciduals and packages.
  - ...
- IBM SPSS Crime Prediction and Prevention.
  - ...
- Chicago "Heat List".
  - 420 names.
  - 500x more likely to commit violent crimes?
  - Distributed to police officers.
- PRECOB
 - Used throughout Germany and Switzerland.
 - Used to forecast burglaries and other repeat-offenses.
- Similar systems
  - Medical prediction based on personal data and stats.
  - Security clearance for govt job applicants.
- US law.
  - Suspiscion.
    - Must look at the whole pictures (totality of the circumstances).
    - Must make a balanced assessment of the relative weights.
  - How much does the US govt really need?
    - ~90% beyoud a reasoable doubt.
    - ...
    - ~30% reasonable suspiscion.
    - Can an algorightm reach 30% suspiscion alone? 60%? 90%?
    - Must have suspiscion before, not after, intervening.
  - Totality of the circumstances.
    - Can the algorithm keep up?
      - Not realtime, not enough (all!) data.
    - Algorithm as one piece in the totality of the circumstances.
    - Bad underlying data, noise in training data, biased data.
  - Acceptable error rate?
    - 1% error rate is still a huge number of people who will be affected.
    - Database errors.
    - Human error.
    - Software error.
- Concerns.
  - Feedback loop.
    - Biases will be persisted.
- Positives pars?
  - Crime reduction shown in cities where software has been used.
  - May or may not be because of software.
- How to eliminate bias?
  - Humans are involved.
  - Initial selection is biased.

