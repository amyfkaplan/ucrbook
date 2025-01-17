# Offenses Known and Clearances by Arrest {#offenses_known}





The Offenses Known and Clearances by Arrest dataset - often called Return A, "Offenses Known" or, less commonly, OKCA - is the oldest and most commonly used dataset and measures crimes reported to the police. For this reason it is used as the main measure of crime in the United States and I tend to call it the "crimes dataset." This data includes the monthly number of crimes reported to the police or otherwise known to the police (e.g. discovered while on patrol) for a small selection of crimes, as well as the number of crimes cleared by arrest or by "exceptional means" (a relatively flawed and manipulable measure of whether the case is "solved"). It also covers the number reported but found by police to have not occurred.  Since this data has monthly agency-level crime information it is often used to measure crime trends between police agencies and over time. The data uses something called a Hierarchy Rule which means that in incidents with multiple crimes, only the most serious is recorded - though in practice this affects only a small percent of cases, and primarily affects property crimes.

## Which crimes are included?

This data set contains information on the number of "Index Crimes" (sometimes called Part I crimes) reported to each agency. These index crimes are a collection of eight crimes that, for historical reasons based largely by perceived importance and reliable of their reporting in the 1920's when the UCR program was first developed, are used as the primary measure of crime today. Other data sets in the UCR, such as the Arrests by Age, Sex, and Race data and the Hate Crime data have more crimes reported. 

The crimes are, in order by the Hierarchy Rule (which we'll discuss next):

1. Homicide     
    + Murder and non-negligent manslaughter   
    + Manslaughter by negligence   
2. Rape     
    + Rape     
    + Attempted rape     
3. Robbery     
    + With a firearm     
    + With a knife of cutting instrument     
    + With a dangerous weapon not otherwise specified     
    + Unarmed - using hands, fists, feet, etc.     
4. Aggravated Assault (assault with a weapon or causing serious bodily injury)     
    + With a firearm     
    + With a knife of cutting instrument     
    + With a dangerous weapon not otherwise specified     
    + Unarmed - using hands, fists, feet, etc.     
5. Burglary     
    + With forcible entry     
    + Without forcible entry      
    + Attempted burglary with forcible entry     
6. Theft (other than of a motor vehicle)     
7. Motor Vehicle Theft     
    + Cars     
    + Trucks and buses     
    + Other vehicles          
8. Arson     
9. Simple Assault     


Arson is considered an index crime but is not reported in this data - you need to use the separate Arson data set of the UCR to get access to arson counts. See Chapter \@ref(arson) for an overview of the Arson data. The ninth crime on that list, simple assault, is not considered an index crime but is nevertheless included in this data. 

Each of the crimes in the list above, and their subcategories, are included in the UCR data. In most news and academic articles, however, you'll see them reported as the total number of index crimes, summing up categories 1-7 and reporting that as "crime." These index crimes are often divided into violent index crimes - murder, rape, robbery, and aggravated assault - and property index crimes - burglary, theft, motor vehicle theft. 

### Hierarchy Rule

This dataset uses what is called the Hierarchy Rule where only the most serious crime in an incident is reported (except for motor vehicle theft and arson, which are always included). For example if there is an incident where the victim is robbed and then murdered, only the murder is counted as it is considered more serious than the robbery. That the data uses the Hierarchy Rule is an oft-cited (by academics, reporters, random people on Twitter) criticism of the data that are, in my opinion, overblown. 

In practice, the Hierarchy Rule has only modest effects on the data, undercounting few crimes. Though the Hierarchy Rule does mean this data is an under-count, data from other sources indicate that it isn't much of an under count. The FBI's other data set, the National Incident-Based Reporting System (NIBRS) contains every crime that occurs in an incident (i.e. it doesn't use the Hierarchy Rule). Using this we can measure how many crimes the Hierarchy Rule excludes (Most major cities do not report to NIBRS so what we find in NIBRS may not apply to them). In over 90% of incidents, only one crime is committed. Additionally, when people talk about "crime" they usually mean murder which, while incomplete to discuss crime, means the UCR data here is accurate on that measure.

The FBI also released a report [available here](https://ucr.fbi.gov/nibrs/2014/resource-pages/effects_of_nibrs_on_crime_statistics_final.pdf) in 2015 that directly examined this issue by taking NIBRS data from 2014 and examined how NIBRS data (which includes all crimes) compares to using the Hierarchy Rule and keeping only the most serious crime. Figure \@ref{fig:fbiHierarchy} is a screenshot from their report showing the percent increases in crimes when including all crimes in an incident relative to following the Hierarchy Rule. They find that 10.6% of incidents have multiple crimes occurring, which is similar to other years that I have examined myself. For violent crime, murder and rape have no change; for the remaining violent crimes - robbery and aggravated assault - crimes increased by 0.6%.^[Murder is not shown in this figure since murder is always reported so cannot change.] Burglary increased by 1% and the largest increases came from theft and motor vehicle theft, increasing by 2.6% and 2.7%, respectively. Curiously motor vehicle theft increased even though the FBI's documentation for this data says that it is exempt from the Hierarchy Rule and should always be reported. This suggests either non-compliance or that the manual is incorrect.


<div class="figure">
<img src="images/fbi_hierarchy.PNG" alt="The FBI's findings of how crime reporting changes when using the Hierarchy Rule using NIBRS 2014 data." width="354" />
<p class="caption">(\#fig:fbiHierarchy)The FBI's findings of how crime reporting changes when using the Hierarchy Rule using NIBRS 2014 data.</p>
</div>

So using the Hierarchy Rule does undercount crime, but this is a small undercounting and is primarily led by property crime. Violent crime is only slightly undercounted. Please keep in mind that this is for crimes that the police record and is unaffected by outside decisions like what the district attorney charges or what the defendant is ultimately convicted of. 

### The problem with using index crimes 

The biggest problem with index crimes is that it is simply the sum of 8 (or 7 since arson data usually isn't available) crimes. Index crimes have a huge range in their seriousness - it includes both murder and theft. This is clearly wrong as 100 murders is more serious than 100 thefts. This is especially a problem as less serious crimes (theft mostly) are far more common than more serious crimes (in 2017 there were 1.25 million violent index crimes in the United States. That same year had 5.5 million thefts.). So index crimes under-count the seriousness of crimes. Looking at total index crimes is, in effect, mostly just looking at theft.

This is especially a problem because it hides trends in violent crimes. San Francisco, as an example, has had a huge increase in index crimes in the last several years. When looking closer, that increase is driven almost entirely by the near doubling of theft since 2011. During the same years, violent crime has stayed fairly steady. So the city isn't getting more dangerous but it appears like it is due to just looking at total index crimes.

Many researchers divide index crimes into violent and nonviolent categories, which helps but is still not entirely sufficient. Take Chicago as an example. It is a city infamous for its large number of murders. But as a fraction of index crimes, Chicago has a rounding error worth of murders. Their 653 murders in 2017 is only 0.5% of total index crimes. For violent index crimes, murder makes up 2.2%. What this means is that changes in murder are very difficult to detect. If Chicago had no murders this year, but a less serious crime (such as theft) increased slightly, we couldn't tell from looking at the number of index crimes.


## Important variables

For each crime we have four different categories indicating the number of crimes actually committed, the number cleared, and the number determined to not have occurred. 

### Actual crimes

This is the number of offenses that occurred, simply a count of the number of crimes that month. For example if 10 people are murdered in a city the number of "actual murders" would be 10. 

### Total cleared crimers

A crime is cleared when an offender is arrested or when the case is considered cleared by exceptional means. When a single offender for a crime is arrested, that crime is considered cleared. If multiple people committed a crime, only a single person must be arrested for it to be cleared, and as the UCR data is at the offense level, making multiple arrests for an incident only counts as one incident cleared. So if 10 people committed a murder and all 10 were arrested, it would report one murder cleared not 10. If only one of these people are arrested it would still report one murder cleared - the UCR does not even say how many people commit a crime.

A crime is considered exceptionally cleared if the police can identify the offender, have enough evidence to arrest the offender, know where the offender is, but is unable to arrest them. Some examples of this are the death of the offender or when the victim refuses to cooperate in the case. 

Unfortunately, this data does not differentiate between clearances by arrest or by exceptional means. For a comprehensive report on how this variable can be exploited to exaggerate clearance rates, see [this report by ProPublica](https://www.propublica.org/article/when-it-comes-to-rape-just-because-a-case-is-cleared-does-not-mean-solved) on exceptional clearances with rape cases. 

### Crimes cleared Where all offenders are under 18 years old

This variable is very similar to Total Cleared except is only for offenses in which **every** offender is younger than age 18. 

### Unfounded crimes

An unfounded crime is one in which a police investigation has determined that the reported crime did not actually happen. For example I observed during a ride-along a report of a burglary where the homeowners said that they came home and the front door was open and they thought it might have been their son who forgot to close it but could also be a burglar so they called the police just in case. This would be recorded as a burglary and if it turned out to be the son, the police would then record this as an unfounded burglary. 

Other unfounded crimes would include when someone reports a crime but later says that the report wasn't true. For example, a person could report a burglary to the police to collect insurance money on the items they claim was stolen. If the police discover this they would unfound the case - and the lying to the police and fraud would not be counted as neither of those are crimes included in this dataset. 

<div class="figure">
<img src="offenses_known_files/figure-html/phillyRapeUnfound-1.png" alt="The annual number of actual and unfounded rapes in Philadephia, PA, 1960-2018." width="672" />
<p class="caption">(\#fig:phillyRapeUnfound)The annual number of actual and unfounded rapes in Philadephia, PA, 1960-2018.</p>
</div>

<div class="figure">
<img src="offenses_known_files/figure-html/phillyRapeUnfoundPercent-1.png" alt="The percent of reported rapes that the police recorded as unfounded in Philadephia, PA, 1960-2018." width="672" />
<p class="caption">(\#fig:phillyRapeUnfoundPercent)The percent of reported rapes that the police recorded as unfounded in Philadephia, PA, 1960-2018.</p>
</div>

## Number of months reported

UCR data is reported monthly though even agencies that decide to report their data may not do so every month. As we don't want to compare an agency which reports 12 months to one that reports fewer, the variable *number_of_months_reported* is way keep only agencies that report 12 months, or deal with those that report fewer. 


## Important issues

### Rape definition change

The FBI changed the definition of rape for UCR data starting in 2013 to a broader definition than the older definition, which is commonly called the "legacy definition" or "legacy" or "historical" rape. The legacy definition is "the carnal knowledge of a female **forcibly** and against her will" (emphasis added). This means that only rape is only included in UCR data when it is a female (or any age, there is no differentiation for child victims) forcibly vaginally penetrated by a penis. This is a narrow definition and excludes a number of sexual acts that people may consider rape such as forced oral or   sex, and cases with a male victim. 

The new (and current) definition "penetration, no matter how slight, of the vagina or anus with any body part or object, or oral penetration by a sex organ of another person, without the consent of the victim." Starting in 2013, rape has a new, broader definition in the UCR to include oral and anal penetration (by a body part or object) and to allow men to be victims. The new definition is: "Penetration, no matter how slight, of the vagina or anus with any body part or object, or oral penetration by a sex organ of another person, without the consent of the victim." The previous definition included only forcible intercourse against a woman. This definition is far broader and is effectively any non-consensual sexual act. It also includes male victims though the data does not differentiate between male or female (or any other gender) victims. 
 
Both the current and legacy definitions exclude statutory rape and incest other than forcible incest. They both also include lack of consent as cases where the victim cannot give consent, such as if they are too young or are mentally or physically incapacitated - they specifically give the example of being temporarily incapacitated through drugs or alcohol.

As this revised definition is broader than the original one post-2013, rape data is not comparable to pre-2013 data. 2013, however, is simply the year that the FBI changed the definition which means that agencies should have changed their reporting to the new definition. As might not be too surprising, not all agencies followed this requirement. We'll look at four examples to show when there is clear evidence that the agency did change their definition in 2013, when it's clear they did so a year later, when it's unclear exactly when they made the change, and when the agency seems to not follow the change at all. 

We'll start with the Philadelphia Police Department in Philadelphia, PA, shown in Figure \@ref(fig:rapePhilly) which shows the annual number of rapes from 2000-2018. It's declining slowly but steadily over the 2000-2012 time period until spiking sharply in 2013. Since the rape definition change in 2013 is far broader than previous year's definition, this makes sense. A broader definition should lead to a sudden increase in reported rapes if the agency is reporting correctly. 

<div class="figure">
<img src="offenses_known_files/figure-html/rapePhilly-1.png" alt="The annual number of rapes reported in Philadelphia, Pennsylvania, 2000-2018." width="672" />
<p class="caption">(\#fig:rapePhilly)The annual number of rapes reported in Philadelphia, Pennsylvania, 2000-2018.</p>
</div>

In comparison, New York City has the sudden spike a year later, which indicates that they didn't start using the new definition until 2014. Figure \@ref(fig:rapeNYC) shows that rape is fairly steady, though increasing, in the years leading up to 2013 and has almost no change from 2012 to 2013, but a huge increase in 2014 and then steadily increases from there, spiking again in 2018. This seems like a fairly clear indicator that NYC simply didn't follow the new definition until 2014. 

<div class="figure">
<img src="offenses_known_files/figure-html/rapeNYC-1.png" alt="The annual number of rapes reported in New York City, 2000-2018." width="672" />
<p class="caption">(\#fig:rapeNYC)The annual number of rapes reported in New York City, 2000-2018.</p>
</div>

Less clear is what's happening in San Francisco, California, shown in Figure \@ref(fig:rapeLA). 
Here we do see an increase in 2013 which while it appears small on the graph is actually a 49% increase from 2012. Then there is a much larger spike in 2014 - a 120% increase - which may suggest that part of the agency started following the new definition in 2013 and the remainder followed in 2014. However, large increases or decreases are relatively common in San Francisco so it could also be that the agency only switched to the new definition in 2014 and the spike in 2013 is just a coincidence 

<div class="figure">
<img src="offenses_known_files/figure-html/rapeLA-1.png" alt="The annual number of rapes reported in San Francisco, California, 2000-2018." width="672" />
<p class="caption">(\#fig:rapeLA)The annual number of rapes reported in San Francisco, California, 2000-2018.</p>
</div>

Finally, we'll look at Jackson Police Department in Mississippi where the definition change seems to have had no effect. As seen in Figure \@ref(fig:rapeJackson), reported rapes start to undulate in 2010 with 2013 data perfectly in line with the before and after trends - no sign that there is a change in reporting. This suggests that Jackson simply did not follow the definition change and continues to report using the old definition. 

<div class="figure">
<img src="offenses_known_files/figure-html/rapeJackson-1.png" alt="The annual number of rapes reported in Jackson, Mississippi, 2000-2018." width="672" />
<p class="caption">(\#fig:rapeJackson)The annual number of rapes reported in Jackson, Mississippi, 2000-2018.</p>
</div>

My takeaway from this is that rape should not be used at all for years after 2012. While the definition change makes pre-2013 and 2013+ years non-comparable, the differences in agency responses to this change - i.e. if they follow the rules or not - is such a mess that the data is too flawed to use. 

### The decline of manslaughter

This data contains two different crime subcategories for homicide: murder and non-negligent manslaughter, and manslaughter by negligence. The first is our measure of murder, and it includes everything we traditionally think of when it comes to murder - shootings, stabbings, strangulation, basically any intentional killing of another person.^[Attempted murder is usually classified as an aggravated assault.] Suicides, killing a fetus, and accidental killings (e.g. car crashes) are not considered murders.^[Even the intentional killing of a fetus is classified as an aggravated assault against the mother, not a murder of the fetus.] The second, manslaughter by negligence - usually called just "manslaughter" - is when someone kills another person through "gross negligence" but does not kill them intentionally. This can include accidental killings when the death was caused by gross negligence. The FBI provide examples of this as kids playing with guns and shooting each other (and not knowing the gun was loaded) or a hunter accidentally shooting someone while hunting. 

I would assume that manslaughter by negligence would remain at a relatively steady rate - though increasing in raw numbers as population increases - as it is due to largely unintentional behavior that would be unaffected by crime-reduction policies.^[Though policies that encourage people to lock up their guns would likely reduce manslaughter by negligence.] I was wrong though. One of the most curiously findings from my exploration of this data is the sudden and national decline in manslaughter by negligence in the 1970s - and the extremely high number of manslaughter before that. Figure \@ref(fig:manslaughterVsMurder) shows the annual number of murders, manslaughter, and the sum of the two nationwide from 1960-2018. This just sums up the total reported counts from every agency each year so part of the increase is simply due to more agencies reporting as the year gets closer to the present day - so please pay attention to the diverging paths of each crime, not the trend for the individual crime over time.

Murder is always more common than manslaughter 



<div class="figure">
<img src="offenses_known_files/figure-html/manslaughterVsMurder-1.png" alt="The annual number of murder and non-negligent manslaughter, manslaughter by negligence, and the sum of the two, nationwide from 1960-2018." width="672" />
<p class="caption">(\#fig:manslaughterVsMurder)The annual number of murder and non-negligent manslaughter, manslaughter by negligence, and the sum of the two, nationwide from 1960-2018.</p>
</div>

Figure \@ref(fig:manslaughterPercent) shows another way to look at this data: manslaughter as a percent of reported murder. In the early years of our data manslaughter was fairly common, with about 70-80% as many manslaughters reported as murders. This declined sharply in the mid-1960s until there were around 45% as many manslaughters as murders in the mid-1970s. Again this declined until it was about 4% in 1980, and it has remained around there ever since.  

<div class="figure">
<img src="offenses_known_files/figure-html/manslaughterPercent-1.png" alt="Reported manslaughter by negligence as a percent of reported murder and non-negligent manslaughter, nationwide 1960-2018." width="672" />
<p class="caption">(\#fig:manslaughterPercent)Reported manslaughter by negligence as a percent of reported murder and non-negligent manslaughter, nationwide 1960-2018.</p>
</div>

