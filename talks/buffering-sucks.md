# Buffering sucks!

*Buffering sucks! Why we see regular buffering when watching online video. What internet service providers could do to reduce buffering and why big players refuse to act. An attempt of calculating the economic cost of buffering.*

Fredy Kuenzler

- https://events.ccc.de/congress/2015/Fahrplan/events/7530.html
- https://media.ccc.de/v/32c3-7530-buffering_sucks


## Talk notes

- Invented the "fastest internet in Switzerland" (init7, fiber7 in 2014)
    - Doing internet/linux for 20-25 years.
    - Politician for the social democrats. Part of the group of internet exports.
- Buffering root causes.
    - Streaming video.
        - Source can be too far away. CDNs are popular though.
        - Adaptive streaming, but downgrades are not fun.
        - Routing/algorithm matches; source or CDN server path.
    - "The caller pays..."
        - Who is making the call in an IP connection?
        - 95% of traffic comes from server to client, even though client imitates transfer.
        - There's no alternative way to reach a user; the user's ISP has to be involved.
    - Broadband provides are not keen on upgrading interconnection capacity.
        - Passive-aggressive behavior.
        - Driven by financial gains, not technical reasoning.
        - End-customers are suffering.
        - Typical client:server traffic ratio is 1:5 to 1:10 (outbound:inbound).
        - If the ration is not near an agreed 1:1, someone has to pay -- the content providers pays.
        - ISPs can charge both content deliverers and end-users for more bandwidth -- double-sided market.
    - Cost of traffic congestion.
        - Car traffic congestion is costly -- 509€ per household per year -- according to official study.
        - "Reservationslohn" is 5€ per hour; "minimum salary".
        - 1 minute of waiting per day; 6 hours; 365/year; 30€ per year; 900M€ per year in Germany.
        - ISPs slow interconnections are part of the traffic congestion problem.
        - With the double-sided market, ISPs make a few million €. The loss is much higher.
        - Should interconnections be regulated in the favor of the end-users?

