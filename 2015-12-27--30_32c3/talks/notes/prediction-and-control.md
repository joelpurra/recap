# Prediction and Control

*Mass quantities of data are being incorporated into predictive systems in an ever-broadening set of fields. In many cases, these algorithms operate in the dark and their use has implications both intentional and unintentional. This talk will cover some of the fairness and accountability issues involved in controlling algorithms for media, policy, and policing.*

Jennifer Helsby

- https://events.ccc.de/congress/2015/Fahrplan/events/7449.html
- https://media.ccc.de/v/32c3-7449-prediction_and_control


## Talk notes

- Data.
    - We give away data on the web, through or cellphones, on our wrists.
- Decision making.
    - Human decisions are slow, biased, not transparent, difficult to audit.
    - Algorithmic decisions are fast, unbiased?, transparent?, can audit?.
- Data -> inference -> action.
- Usage.
    - Google search predictions, personalized results.
    - Facebook wall recommendations.
    - Political campaigns target voters.
    - Police can focus efforts.
    - Set the temperature of our houses.
- Advantages.
    - Automate rote tasks.
    - Make things more efficient.
    - Save money.
- Algorithms.
    - Can have serious implications.
    - Chinese social credit system.
        - Inputs.
            - Ranks financial records.
            - Criminal history.
            - Drivers license history.
            - Some medical info.
            - Purchase history.
            - Social media monitoring.
            - Social network analysis.
        - Goal is to "Carry forward sincerity and traditional virtues."
        - Can give social perks; hotels will give you perks.
    - Questions.
        - Is information about the system open?
        - How can you change your score?
        - Is it a self-fulfilling prophecy, where you eventually "become" your (initially erroneous) score.
- What do we want?
    - Privacy.
    - Fairness.
- Predictive policing.
    - Keeping track if people will be involved in crime, as criminal or victim.
    - Tools
        - Could be done on individual level (profiling), but sold as geographical areas in the tools.
        - Hitachi, Predpol, Hunchlab, Azavea sell these kinds of systems.
    - Fairness concerns.
        - Similar people going through a similar process may have different outcomes.
            - Similar people are treated similarly.
        - Group fairness for protected groups.
            - Similar people are treated similarly.
        - Grouping by surname?
        - ...
    - Training data issues.
        - Crime database contains only crimes detected by police.
        - Gun violence reported more often than fraud.
        - Effects of biased policing; among marijuana smokers in the US, black citizens get arrested 4x more often than white.
        - Race and location are correlated in the US.
            - Machine learning systems can learn sensitive features.
        - No opt-out; citizens need more information about these systems.
        - Should citizens push for audits?
    - What are these systems doing?
        - Hard to tell.
        - Google's search is personalized, so by definition each person sees only one possible outcome among many.
    - Influence voting.
        - Research with several groups; manipulated and control.
        - Testing voting outcomes.
        - Modifying search results page for part groups; subtly adding or removing results from the first result page.
        - Reached 20% voter shift.
        - That margin can change about 25% of elections worldwide.
    - Behavioral insights team.
        - UK group created by David Cameron.
        - "The nudge unit."
        - Use behavioral research to encourage people to make "the right decisions" in their life. (As defined by the government.)
        - The US are creating their own group.
    - Optimization.
        - For websites, it's easy.
            - Google wants you to use their services more.
            - Facebook wants you to spend more time, click on more items.
            - All this leads to profit.
            - 40% of people get their news from Facebook.
            - The system won't optimize for some kinds of news; entertainment is an easier click/sell than sad news with dead corpses.
        - Politics.
            - Swing votes for undecided voters.
        - Government systems.
            - Optimizing for compliance; see the police systems.
- Awareness.
    - Because our world view is limited by big data algorithm outputs, what we perceive as the "free world" is limited. We can't even see the barb wire.
- ...
    - Twins getting drivers license could not, because of fraud detection software at the DMV.
    - Automated license plate readers (ALPR) is used in San Francisco.
        - SFPD got a false hit on a car.
        - Pulled over 47 year old woman in her own car.
        - Had her kneel at gun point, patted down, searched car.
- Auditing.
    - With inputs and outputs, tests can be performed.
    - People have tested the Obama campaign's targeted emails.
        - 200 emails submitted for analysis.
    - Potential legal problems when testing.
    - People have tested the Google SERP.
        - Testing ads on the SERP.
        - Creating different users, recording ad networks output.
        - Differ profiles by gender.
        - Women less likely to be shown ads for high-paid jobs on Google.
- Who is in control?
    - Minimizing the amount of data is useful.
    - Auditing tools.
        - Sunlight.
        - Adfisher.
        - Tor for "generic profiles".
    - View the landscape.
        - Poor vs rich see different "internets".
        - Men vs women as well.
    - Obfuscation.
        - "Adnaseum" Firefox plugin clicks on every ad on every page.
- Policy.
    - Regulation.
    - Lack of ethics review in private companies.
        - See Facebook wall/stream experiments.
    - Auditing.
        - Third-party.
        - Some companies don't want Auditing.
- Closing thoughts.
    - Algorithmic systems need appropriate oversight in order to be controlled.
    - Hacking and privacy advocacy community has an important role in the fight.


---

Part of [Recap](https://github.com/joelpurra/recap)

