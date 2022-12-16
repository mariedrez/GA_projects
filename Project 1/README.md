# Project 1: Standardized Test Analysis


## Problem Statement

You work for the ACT inc, the board that administers an entrance exam used by most colleges and universities to make admissions decisions. <br>

ACT inc has asked you to advise marketing decisions to high school students on sitting for the ACT should they intend to enrol in college for their intended school major. Since enrolling students can choose to sit for either the SAT or the ACT, the board is concerned about improving the ACT participation rates in the coming school year. <br>

Your presentation and report should be geared toward non-technical executives of ACT inc and you will use the provided data and outside research to make recommendations about how the company might work to increase the participation rate in a state of your choice.

## External Research

In 2019, more than 1.72 million graduates (estimated 52% of the US high school graduands) sat for the ACT <a href="https://www.act.org/content/dam/act/unsecured/documents/National-CCCR-2019.pdf" target="_blank"><sup>1</sup></a>.
This is a slight drop from the 1.9 million ACT candidates (or estimated 55% of the graduating batch) reported in 2018<a href="https://www.washingtonpost.com/education/2018/10/23/sat-reclaims-title-most-widely-used-college-admission-test/" target="_blank"><sup>2</sup></a>. Meanwhile, over 2.2 million graduates sat for the SAT, with a 4% increase from the previous year<a href="https://newsroom.collegeboard.org/over-22-million-students-class-2019-took-sat-largest-group-ever" target="_blank"><sup>3</sup></a>. Evidence here suggests that the ACT is becoming relatively less popular over the years.

This can be traced to by the steady gain in market share by the College Board that owns the SAT, through "revising the test and entering into deals with numerous states and school systems to give students the exam" <a href="https://www.washingtonpost.com/education/2018/10/23/sat-reclaims-title-most-widely-used-college-admission-test/" target="_blank"><sup>4</sup></a>. Similar arrangements exist for the ACT as well, that allow students in said states and school systems to sit for the exam on a school day at no charge. As it stands, 16 states allow students to sit for the ACT exams at no charge, while 11 states offer students to sit for the SAT at no charge<a href="https://www.collegeraptor.com/getting-in/articles/act-sat/states-act-sat-given-free/" target="_blank"><sup>5</sup></a>. 

Applications to sit for the ACT and SAT cost a considerable sum. Self-sponsored ACT candidates pay \\$63 to sit for the exams, and an additional \\$25 to be tested on an optional Writing component. On the other hand, self-sponsored SAT candidates pay \\$60 to sit for the exams <a href="https://blog.prepscholar.com/act-vs-sat" target="_blank"><sup>6</sup></a>.


How prevalent is it that students sit for both tests? While colleges generally do not discriminate between the ACT and the SAT, a significant percentage of students sit for both exams<a href="https://www.princetonreview.com/college-advice/4-reasons-to-take-both-sat-and-act" target="_blank"><sup>7</sup></a>. Among many reasons to sit for both exams include: 
- the ability to offer additional information on one's strengths to the Admissions Committe of one's intended college <a href="https://www.nytimes.com/2020/05/26/learning/should-students-be-required-to-take-the-sat-and-act-to-apply-to-college.html" target="_blank"><sup>8</sup></a>, 

- being able to prepare more efficiently in the event that one is intending to re-sit either/both exams to earn target scores, and 
- increasing one's chances of earning merit-based financial aid upon enrolment to college <a href="https://www.princetonreview.com/college-advice/4-reasons-to-take-both-sat-and-act" target="_blank"><sup>9</sup></a>.

## Data Science workflow

A data science workflow was undertaken to organise the processes for this project. 

Firstly, a problem statement was defined and established. 

Secondly, data from credible sources that contained suitable datasets were imported using Pandas. Appropriate datasets that were identified are: ACT participation rates and test scores from 2017 to 2019, as well as the SAT participation rates and test scores in 2019. 

Next, data cleaning was carried out to ensure that data is complete, in the correct formats and accurate. Upon cleaning, the various datasets were merged into a single DataFrame.

Then, an exploratory data analysis was conducted to determine the trends over the years and to uncover any interesting insights across the datasets. 

Thereafter, data visualizations were plotted to highlight the trends and outliers about the populations.

Finally, based on the analyses, recommendations were passed about how ACT inc can carry out a data-driven campaign to promote higher participation rates in its exams in the following years.

## Data Dictionary

|Feature|Type|Dataset|Description|
|:-----------|:---|:--------|:---------------------------------------------------------------------------------|
|act_free|bool|final_csv|Expresses whether students in a state can take the ACT for free. 1= True, 0= False|
|act_part_rate |*float*|final_csv|ACT participation rate (in percentage) in a given year. 0.22 means 22%| 
|act_com_score|*float*|final_csv|ACT Composite score for a given state in a given year. act17_com_score refers to the composite score in the year 2017. (Possible score range 1-36)| 
|part_pct_change|*float*|final_csv|State participation in a given exam as percentage of national average participation| 
|sat_free|*bool*|final_csv|Expresses whether students in a state can take the SAT for free. 1= True, 0= False| 
|sat19_part_rate|*float*|final_csv|SAT participation rate (in percentage) in the year 2019. 0.22 means 22%|
|sat19_total_score|*float*|final_csv|Average total score for a given state in the year 2019, computed using EWR and Math scores (Possible score range 400-1600)|  
|score_pct_change|*float*|final_csv|State average score in a given exam as percentage of national average score| 
|state|*object*|final_csv|Names of all US states and the District of Columbia| 


# Summary of analysis

In general, participation rates for both the ACT and the SAT has a strong positive correlation with whether students can sit for the respective exams for free. While it is likely that the removal of financial costs and the ability to sit for the exam conveniently on a school day encouraged more students to participate, it should be noted that some states had made the exams mandatory for high school graduands. For example, Montana, Nebraska and Nevada which set the ACT as the sole high school exit exam reported a 100% ACT participation rate. Similarly, Connecticut, Maine, New Hampshire and West Virginia which set the SAT as the sole high school exit exam reported a 100% SAT participation rate.

## Conclusions & Recommendations

In general, participation rates for both the ACT and the SAT has a strong positive correlation with whether students can sit for the respective exams for free. While it is likely that the removal of financial costs and the ability to sit for the exam conveniently on a school day encouraged more students to participate, it should be noted that some states had made the exams mandatory for high school graduands. For example, Montana, Nebraska and Nevada which set the ACT as the sole high school exit exam reported a 100% ACT participation rate. Similarly, Connecticut, Maine, New Hampshire and West Virginia which set the SAT as the sole high school exit exam reported a 100% SAT participation rate.

While the lowering of barriers had motivated greater exam participation, it is seen that overall state averages simultaneously suffer for both the ACT and SAT respectively. However, this should not be the impetus to make the ACT fees to be fully student-borne nor to make the ACT optional for high school graduands across the country. It is a curious trend that bears further study. For example, studies should be furthered to query and analyse students and teaching faculties' perception of the ACT's relevance in college admissions, as well as the standard of preparation for the ACT in states which have made it a prerequisite for high school graduation.

To maintain high participation rates in states that make it mandatory, I suggest keeping the contracts with these states and school systems  that administer ACT for free. This significantly lowers barriers to entry for students in underserved populations that belong to more than one of these categories: from minority ethnicity, from low-income household, from family where parents are not college graduates.

Secondly, to add focus on marketing the ACT exam in states and school systems where SAT is prevalent choice. By angling it as a welcome additional metric to profile a high-achieving student, ACT, inc can increase its market share of the test-taking population and thus participation rates. 

Thirdly, to update test conditions to make it more equitable for all students. Aagard postulates that there is a significant relationship between testing condition and student test scores for students of various capabilities <a href="https://www.thefreelibrary.com/The+relationship+between+testing+condition+and+student+test+scores.-a0126582635" target="_blank"><sup>10</sup></a>. This can help to boost performance of low-achieving students who form bulk of underserved student population and improve their college admission chances.
