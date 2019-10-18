---
title: "EUS, Kerberos, SSL and OUD a guideline"
subtitle: "Demo Scripts, Examples and Exercises"
author: [Stefan Oehrli]
date: "2018 November 01"
tvddocversion: 0.9
papersize: a4 
listings-disable-line-numbers: true
titlepage: true
toc: true
toc-own-page: true
mainfont: Nunito Sans SemiBold
monofont: Courier New
---

# Table

| ID | Test  | Comment   |
|----|-------|-----------|
| 1  | wieso | halt Here's a sentence with a footnote. |
| 2  | wieso | halt text |
| 3  | wieso | halt text |
| 4  | wieso | halt text |

Table: Your Caption


| Version        | Windows | HPUX | AIX    | Solaris | Linux 64bit |
|----------------|---------|------|--------|---------|-------------|
| RDBMS 18.1.0.0 |         | n/a  |        |         |             |
| RDBMS 18.2.0.0 |         | n/a  | **Ok** |         | ***Ok***    |
| RDBMS 18.3.0.0 |         | n/a  |        | NOk     |             |
| RDBMS 18.3.0.0 |         |      |        |         |             |
| RDBMS 18.1.0.0 |         |      |        |         |             |

\begin{longtable}[]{llllllll}
\caption[Nam liber tempor cum soluta nobis eleifend option congue.]{Nam liber tempor cum soluta nobis eleifend option congue nihil imperdiet doming id quod mazim placerat facer possim assum. Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.} \\
\toprule
Test Nr. & Position & Radius & Rot & Grün & Blau &
beste Fitness & Abweichung\tabularnewline
\midrule
\endhead
1 & 20 \% & 20 \% & 20 \% & 20 \% & 20 \% & 7,5219 &
0,9115\tabularnewline
2 & 0 \% & 25 \% & 25 \% & 25 \% & 25 \% & 8,0566 &
1,4462\tabularnewline
3 & 0 \% & 0 \% & 33 \% & 33 \% & 33 \% & 8,7402 & 2,1298\tabularnewline
4 & 50 \% & 20 \% & 10 \% & 10 \% & 10 \% & 6,6104 &
0,0000\tabularnewline
5 & 70 \% & 0 \% & 10 \% & 10 \% & 10 \% & 7,0696 &
0,4592\tabularnewline
6 & 20 \% & 50 \% & 10 \% & 10 \% & 10 \% & 7,0034 &
0,3930\tabularnewline
\bottomrule
\end{longtable}


## andere

\begin{tabularx}{1.05\textwidth}{l|l|l|X}
  \hline
  \rowcolor{tvdgray2}\textbf{Name} & \textbf{Visum} &
  \textbf{Funktion / Geschäftsbereich} & \textbf{E-Mail}\\
  \hline
  Miguel Anjo & ami & Senior Consultant / ZH-IMS & miguel.anjo@trivadis.com \\
  \hline
  Patrick Joss & jpa & Senior Consultant / ZH-IMS & patrick.joss@trivadis.com \\
  \hline
  Dirk Nachbar & din & Senior Consultant / BE-IMS & dirk.nachbar@trivadis.com\\
  \hline
  Stefan Oehrli & soe & Solution Manager / BDS & stefan.oehrli@trivadis.com\\
  \hline
\end{tabularx}

text oder so