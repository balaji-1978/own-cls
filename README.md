# own-cls
    \NeedsTeXFormat{LaTeX2e}[1995/12/01]
    \ProvidesClass{aa} [2014/02/03 v1.0a Standard LaTeX document class]
    \newcommand\@ptsize{}
    \newif\if@restonecol
    \newif\if@titlepage
    \@titlepagefalse
    \if@compatibility\else
    \DeclareOption{a4paper}
       {\setlength\paperheight {297mm}%
        \setlength\paperwidth  {210mm}}
    \DeclareOption{a5paper}
       {\setlength\paperheight {210mm}%
        \setlength\paperwidth  {148mm}}
    \DeclareOption{b5paper}
       {\setlength\paperheight {250mm}%
        \setlength\paperwidth  {176mm}}
    \DeclareOption{letterpaper}
       {\setlength\paperheight {11in}%
        \setlength\paperwidth  {8.5in}}
    \DeclareOption{legalpaper}
       {\setlength\paperheight {14in}%
        \setlength\paperwidth  {8.5in}}
    \DeclareOption{executivepaper}
       {\setlength\paperheight {10.5in}%
        \setlength\paperwidth  {7.25in}}
    \DeclareOption{landscape}
       {\setlength\@tempdima   {\paperheight}%
        \setlength\paperheight {\paperwidth}%
        \setlength\paperwidth  {\@tempdima}}
    \fi
    \if@compatibility
      \renewcommand\@ptsize{0}
    \else
    \DeclareOption{10pt}{\renewcommand\@ptsize{0}}
    \fi
    \DeclareOption{11pt}{\renewcommand\@ptsize{1}}
    \DeclareOption{12pt}{\renewcommand\@ptsize{2}}
    \if@compatibility\else
    \DeclareOption{oneside}{\@twosidefalse \@mparswitchfalse}
    \fi
    \DeclareOption{twoside}{\@twosidetrue  \@mparswitchtrue}
    \DeclareOption{draft}{\setlength\overfullrule{5pt}}
    \if@compatibility\else
    \DeclareOption{final}{\setlength\overfullrule{0pt}}
    \fi
    \DeclareOption{titlepage}{\@titlepagetrue}
    \if@compatibility\else
    \DeclareOption{notitlepage}{\@titlepagefalse}
    \fi
    \if@compatibility\else
    \DeclareOption{onecolumn}{\@twocolumnfalse}
    \fi
    \DeclareOption{twocolumn}{\@twocolumntrue}
    \DeclareOption{leqno}{\input{leqno.clo}}
    \DeclareOption{fleqn}{\input{fleqn.clo}}
    \DeclareOption{openbib}{%
      \AtEndOfPackage{%
       \renewcommand\@openbib@code{%
          \advance\leftmargin\bibindent
          \itemindent -\bibindent
          \listparindent \itemindent
          \parsep \z@
          }%
       \renewcommand\newblock{\par}}%
    }
    \ExecuteOptions{letterpaper,10pt,twoside,onecolumn,final}
    \ProcessOptions
    \input{size1\@ptsize.clo}
    \setlength\lineskip{1\p@}
    \setlength\normallineskip{1\p@}
    \renewcommand\baselinestretch{}
    \setlength\parskip{0\p@ \@plus \p@}
    \@lowpenalty   51
    \@medpenalty  151
    \@highpenalty 301
    \setcounter{topnumber}{2}
    \setcounter{bottomnumber}{2}
    \setcounter{totalnumber}{4}
    \renewcommand\topfraction{0.85}
    \renewcommand\bottomfraction{0.85}
    \renewcommand\textfraction{0.15}
    \renewcommand\floatpagefraction{0.7}
    \setcounter{dbltopnumber}{5}
    \renewcommand\dbltopfraction{.7}
    \renewcommand\dblfloatpagefraction{0.7}
    \if@twoside
      \def\ps@headings{%
          \let\@oddfoot\@empty\let\@evenfoot\@empty
          \def\@evenhead{\thepage\hfil\slshape\leftmark}%
          \def\@oddhead{{\slshape\rightmark}\hfil\thepage}%
          \let\@mkboth\markboth
        \def\sectionmark##1{%
          \markboth {\MakeUppercase{%
            \ifnum \c@secnumdepth >\z@
              \thesection\quad
            \fi
            ##1}}{}}%
        \def\subsectionmark##1{%
          \markright {%
            \ifnum \c@secnumdepth >\@ne
              \thesubsection\quad
            \fi
            ##1}}}
    \else
      \def\ps@headings{%
        \let\@oddfoot\@empty
        \def\@oddhead{{\slshape\rightmark}\hfil\thepage}%
        \let\@mkboth\markboth
        \def\sectionmark##1{%
          \markright {\MakeUppercase{%
            \ifnum \c@secnumdepth >\m@ne
              \thesection\quad
            \fi
            ##1}}}}
    \fi
    \def\ps@myheadings{%
        \let\@oddfoot\@empty\let\@evenfoot\@empty
        \def\@evenhead{\thepage\hfil\slshape\leftmark}%
        \def\@oddhead{{\slshape\rightmark}\hfil\thepage}%
        \let\@mkboth\@gobbletwo
        \let\sectionmark\@gobble
        \let\subsectionmark\@gobble
        }
      \if@titlepage
      \newcommand\maketitle{\begin{titlepage}%
      \let\footnotesize\small
      \let\footnoterule\relax
      \let \footnote \thanks
      \null\vfil
      \vskip 60\p@
      \begin{center}%
        {\LARGE \@title \par}%
        \vskip 3em%
        {\large
         \lineskip .75em%
          \begin{tabular}[t]{c}%
            \@author
          \end{tabular}\par}%
          \vskip 1.5em%
        {\large \@date \par}%       % Set date in \large size.
      \end{center}\par
      \@thanks
      \vfil\null
      \end{titlepage}%
      \setcounter{footnote}{0}%
      \global\let\thanks\relax
      \global\let\maketitle\relax
      \global\let\@thanks\@empty
      \global\let\@author\@empty
      \global\let\@date\@empty
      \global\let\@title\@empty
      \global\let\title\relax
      \global\let\author\relax
      \global\let\date\relax
      \global\let\and\relax
    }
    \else
    \newcommand\maketitle{\par
      \begingroup
        \renewcommand\thefootnote{\@fnsymbol\c@footnote}%
        \def\@makefnmark{\rlap{\@textsuperscript{\normalfont\@thefnmark}}}%
        \long\def\@makefntext##1{\parindent 1em\noindent
                \hb@xt@1.8em{%
                    \hss\@textsuperscript{\normalfont\@thefnmark}}##1}%
        \if@twocolumn
          \ifnum \col@number=\@ne
            \@maketitle
          \else
            \twocolumn[\@maketitle]%
          \fi
        \else
          \newpage
          \global\@topnum\z@   % Prevents figures from going at top of page.
          \@maketitle
        \fi
        \thispagestyle{allpage}\@thanks %%%%%%%%%%%%marking
      \endgroup
      \setcounter{footnote}{0}%
      \global\let\thanks\relax
      \global\let\maketitle\relax
      \global\let\@maketitle\relax
      \global\let\@thanks\@empty
      \global\let\@author\@empty
      \global\let\@date\@empty
      \global\let\@title\@empty
      \global\let\title\relax
      \global\let\author\relax
      \global\let\date\relax
      \global\let\and\relax
    }
    \def\@maketitle{%
      \newpage
      \null
      \vskip 2em%
      \begin{center}%
      \let \footnote \thanks
        {\LARGE \@title \par}%
        \vskip 1.5em%
        {\large
          \lineskip .5em%
          \begin{tabular}[t]{c}%
            \@author
          \end{tabular}\par}%
        \vskip 1em%
    %    {\large \@date}%
      \end{center}%
      \par
      \vskip 1.5em}
    \fi
    \setcounter{secnumdepth}{0}
    \newcounter {part}
    \newcounter {section}
    \newcounter {subsection}[section]
    \newcounter {subsubsection}[subsection]
    \newcounter {paragraph}[subsubsection]
    \newcounter {subparagraph}[paragraph]
    \renewcommand \thepart {\@Roman\c@part}
    \renewcommand \thesection {\@arabic\c@section}
    \renewcommand\thesubsection   {\thesection.\@arabic\c@subsection}
    \renewcommand\thesubsubsection{\thesubsection.\@arabic\c@subsubsection}
    \renewcommand\theparagraph    {\thesubsubsection.\@arabic\c@paragraph}
    \renewcommand\thesubparagraph {\theparagraph.\@arabic\c@subparagraph}
    \newcommand\part{%
       \if@noskipsec \leavevmode \fi
       \par
       \addvspace{4ex}%
       \@afterindentfalse
       \secdef\@part\@spart}
    
    \def\@part[#1]#2{%
        \ifnum \c@secnumdepth >\m@ne
          \refstepcounter{part}%
          \addcontentsline{toc}{part}{\thepart\hspace{1em}#1}%
        \else
          \addcontentsline{toc}{part}{#1}%
        \fi
        {\parindent \z@ \raggedright
         \interlinepenalty \@M
         \normalfont
         \ifnum \c@secnumdepth >\m@ne
           \Large\bfseries \partname\nobreakspace\thepart
           \par\nobreak
         \fi
         \huge \bfseries #2%
         \markboth{}{}\par}%
        \nobreak
        \vskip 3ex
        \@afterheading}
    \def\@spart#1{%
        {\parindent \z@ \raggedright
         \interlinepenalty \@M
         \normalfont
         \huge \bfseries #1\par}%
         \nobreak
         \vskip 3ex
         \@afterheading}
    \newcommand\section{\@startsection {section}{1}{\z@}%
                                       {-2.8ex}%
                                       {8.25pt}%
                                       {\raggedright\sectionfont}}
    \newcommand\subsection{\@startsection{subsection}{2}{\z@}%
                                         {-2.95ex}%
                                         {.1ex}%.0001ex
                                         {\raggedright\subsectionfont}}
    \newcommand\subsubsection{\@startsection{subsubsection}{3}{\z@}%
                                         {-2.95ex}%
                                         {.1ex}%11.5pt
                                         {\raggedright\subsubsectionfont}}
    \newcommand\paragraph{\@startsection{paragraph}{4}{\z@}%
                                    {-2.95ex}%
                                        {.1ex}%
                                        {\raggedright\paragraphfont}}
    \newcommand\subparagraph{\@startsection{subparagraph}{5}{\z@}%
                                  {-2.95ex}%
                                           {.1ex}%
                                          {\raggedright\subparagraphfont}}
    \if@twocolumn
      \setlength\leftmargini  {2em}
    \else
      \setlength\leftmargini  {2.5em}
    \fi
    \leftmargin  \leftmargini
    \setlength\leftmarginii  {2.2em}
    \setlength\leftmarginiii {1.87em}
    \setlength\leftmarginiv  {1.7em}
    \if@twocolumn
      \setlength\leftmarginv  {.5em}
      \setlength\leftmarginvi {.5em}
    \else
      \setlength\leftmarginv  {1em}
      \setlength\leftmarginvi {1em}
    \fi
    \usepackage{float,stfloats}
    \usepackage[maxfloats=25,morefloats=7]{morefloats}%
    \usepackage{placeins}
    \FloatBarrier
    \usepackage{fltrace}
    \tracefloats 
    \setlength  \labelsep  {.5em}
    \setlength  \labelwidth{\leftmargini}
    \addtolength\labelwidth{-\labelsep}
    \@beginparpenalty -\@lowpenalty
    \@endparpenalty   -\@lowpenalty
    \@itempenalty     -\@lowpenalty
    \renewcommand\theenumi{\@arabic\c@enumi}
    \renewcommand\theenumii{\@alph\c@enumii}
    \renewcommand\theenumiii{\@roman\c@enumiii}
    \renewcommand\theenumiv{\@Alph\c@enumiv}
    \newcommand\labelenumi{\theenumi.}
    \newcommand\labelenumii{(\theenumii)}
    \newcommand\labelenumiii{\theenumiii.}
    \newcommand\labelenumiv{\theenumiv.}
    \renewcommand\p@enumii{\theenumi}
    \renewcommand\p@enumiii{\theenumi(\theenumii)}
    \renewcommand\p@enumiv{\p@enumiii\theenumiii}
    \newcommand\labelitemi{\textbullet}
    \newcommand\labelitemii{\normalfont\bfseries \textendash}
    \newcommand\labelitemiii{\textasteriskcentered}
    \newcommand\labelitemiv{\textperiodcentered}
    \newenvironment{description}
                   {\list{}{\labelwidth\z@ \itemindent-\leftmargin
                            \let\makelabel\descriptionlabel}}
                   {\endlist}
    \newcommand*\descriptionlabel[1]{\hspace\labelsep
                                    \normalfont\bfseries #1}
    \if@titlepage
      \newenvironment{abstract}{%
          \titlepage
          \null\vfil
          \@beginparpenalty\@lowpenalty
          \begin{center}%
            \bfseries \abstractname
            \@endparpenalty\@M
          \end{center}}%
         {\par\vfil\null\endtitlepage}
    \else
      \newenvironment{abstract}{%
          \if@twocolumn
            \section*{\abstractname}%
          \else
            \small
            \begin{center}%
              {\bfseries \abstractname\vspace{-.5em}\vspace{\z@}}%
            \end{center}%
            \quotation
          \fi}
          {\if@twocolumn\else\endquotation\fi}
    \fi
    \newenvironment{verse}
                   {\let\\\@centercr
                    \list{}{\itemsep      \z@
                            \itemindent   -1.5em%
                            \listparindent\itemindent
                            \rightmargin  \leftmargin
                            \advance\leftmargin 1.5em}%
                    \item\relax}
                   {\endlist}
    \newenvironment{quotation}
                   {\list{}{\listparindent 1.5em%
                            \itemindent    \listparindent
                            \rightmargin   \leftmargin
                            \parsep        \z@ \@plus\p@}%
                    \item\relax}
                   {\endlist}
    \newenvironment{quote}
                   {\list{}{\leftmargin=12pt\rightmargin\leftmargin}%
                    \item\relax}
                   {\endlist}
    \if@compatibility
    \newenvironment{titlepage}
        {%
          \if@twocolumn
            \@restonecoltrue\onecolumn
          \else
            \@restonecolfalse\newpage
          \fi
          \thispagestyle{empty}%
          \setcounter{page}\z@
        }%
        {\if@restonecol\twocolumn \else \newpage \fi
        }
    \else
    \newenvironment{titlepage}
        {%
          \if@twocolumn
            \@restonecoltrue\onecolumn
          \else
            \@restonecolfalse\newpage
          \fi
          \thispagestyle{empty}%
          \setcounter{page}\@ne
        }%
        {\if@restonecol\twocolumn \else \newpage \fi
         \if@twoside\else
            \setcounter{page}\@ne
         \fi
        }
    \fi
    \newcommand\appendix{\par
      \setcounter{section}{0}%
      \setcounter{subsection}{0}%
      \gdef\thesection{\@Alph\c@section}}
    \setlength\arraycolsep{5\p@}
    \setlength\tabcolsep{6\p@}
    \setlength\arrayrulewidth{.4\p@}
    \setlength\doublerulesep{2\p@}
    \setlength\tabbingsep{\labelsep}
    \skip\@mpfootins = \skip\footins
    \setlength\fboxsep{3\p@}
    \setlength\fboxrule{.4\p@}
    \renewcommand \theequation {\@arabic\c@equation}
    \newcounter{figure}
    \renewcommand \thefigure {\@arabic\c@figure}
    \def\fps@figure{htpb}
    \def\ftype@figure{1}
    \def\ext@figure{lof}
    \def\fnum@figure{\figurename\nobreakspace\thefigure}
    \newenvironment{figure}
                   {\let\@makecaption\@makefigcaptiondouble\@float{figure}}
                   {\end@float}
    \newenvironment{figure*}
                   {\let\@makecaption\@makefigcaptiondouble\@dblfloat{figure}}
                   {\end@dblfloat}
    \newcounter{table}
    \renewcommand\thetable{\@arabic\c@table}
    \def\fps@table{tbp}
    \def\ftype@table{2}
    \def\ext@table{lot}
    \def\fnum@table{\tablename\nobreakspace\thetable}
    \newenvironment{table}
                   {\let\@makecaption\@processcaption\@float{table}}
                   {\end@float}
    \newenvironment{table*}
                   {\let\@makecaption\@processcaption\@dblfloat{table}}
                   {\end@dblfloat}
    \newlength\abovecaptionskip
    \newlength\belowcaptionskip
    \setlength\abovecaptionskip{10\p@}
    \setlength\belowcaptionskip{0\p@}
    \usepackage{multicol}%Don't Change the package place
    %%%%%%%%%%%%%%%%%%%%%%%%%%Table Caption%%%%%%%%%%%%%%%%%%%%%
    
    \long\def\@processcaption#1#2{\vspace{\abovecaptionskip}%
    \tablecaptionfont%
      \setbox\@tempboxa=\hbox{{{\tableheadfont #1\ |\ }%
        \tablecaptionfont #2}}%
      \ifdim\wd\@tempboxa>\hsize
      \MakeUppercase{\figheadfont #1\ |\ }% 
    \fontspec{HelveticaNeueLTStd-Bd}{#2}%
      \else
        \hbox to \hsize{\MakeUppercase{\tableheadfont #1\ |\ }%
            \ignorespaces{\tablecaptionfont #2}\hss}
      \fi}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%Common Caption%%%%%%%%%%%%%%%%%%%%%
    
    \long\def\@makecaption#1#2{\vspace{\abovecaptionskip}%
    \figcaptionfont%
      \setbox\@tempboxa=\hbox{{{\figheadfont#1\ |\ }%
        \figcaptionfont#2}}%
      \ifdim\wd\@tempboxa>\hsize
      {\figheadfont#1\ |\ }%
    {\figcaptionfont#2}%
      \else
        \hbox to \hsize{{\figheadfont #1\ |\ }%
            \ignorespaces{\figcaptionfont#2}\hss}
      \fi}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    \DeclareOldFontCommand{\rm}{\normalfont\rmfamily}{\mathrm}
    \DeclareOldFontCommand{\sf}{\normalfont\sffamily}{\mathsf}
    \DeclareOldFontCommand{\tt}{\normalfont\ttfamily}{\mathtt}
    \DeclareOldFontCommand{\bf}{\normalfont\bfseries}{\mathbf}
    \DeclareOldFontCommand{\it}{\normalfont\itshape}{\mathit}
    \DeclareOldFontCommand{\sl}{\normalfont\slshape}{\@nomath\sl}
    \DeclareOldFontCommand{\sc}{\normalfont\scshape}{\@nomath\sc}
    \DeclareRobustCommand*\cal{\@fontswitch\relax\mathcal}
    \DeclareRobustCommand*\mit{\@fontswitch\relax\mathnormal}
    \newcommand\@pnumwidth{1.55em}
    \newcommand\@tocrmarg{2.55em}
    \newcommand\@dotsep{4.5}
    \setcounter{tocdepth}{3}
    \newcommand\tableofcontents{%
        \section*{\contentsname
            \@mkboth{%
               \MakeUppercase\contentsname}{\MakeUppercase\contentsname}}%
        \@starttoc{toc}%
        }
    \newcommand*\l@part[2]{%
      \ifnum \c@tocdepth >-2\relax
        \addpenalty\@secpenalty
        \addvspace{2.25em \@plus\p@}%
        \setlength\@tempdima{3em}%
        \begingroup
          \parindent \z@ \rightskip \@pnumwidth
          \parfillskip -\@pnumwidth
          {\leavevmode
           \large \bfseries #1\hfil \hb@xt@\@pnumwidth{\hss #2}}\par
           \nobreak
           \if@compatibility
             \global\@nobreaktrue
             \everypar{\global\@nobreakfalse\everypar{}}%
          \fi
        \endgroup
      \fi}
    \newcommand*\l@section[2]{%
      \ifnum \c@tocdepth >\z@
        \addpenalty\@secpenalty
        \addvspace{1.0em \@plus\p@}%
        \setlength\@tempdima{1.5em}%
        \begingroup
          \parindent \z@ \rightskip \@pnumwidth
          \parfillskip -\@pnumwidth
          \leavevmode \bfseries
          \advance\leftskip\@tempdima
          \hskip -\leftskip
          #1\nobreak\hfil \nobreak\hb@xt@\@pnumwidth{\hss #2}\par
        \endgroup
      \fi}
    \newcommand*\l@subsection{\@dottedtocline{2}{1.5em}{2.3em}}
    \newcommand*\l@subsubsection{\@dottedtocline{3}{3.8em}{3.2em}}
    \newcommand*\l@paragraph{\@dottedtocline{4}{7.0em}{4.1em}}
    \newcommand*\l@subparagraph{\@dottedtocline{5}{10em}{5em}}
    \newcommand\listoffigures{%
        \section*{\listfigurename}%
          \@mkboth{\MakeUppercase\listfigurename}%
                  {\MakeUppercase\listfigurename}%
        \@starttoc{lof}%
        }
    \newcommand*\l@figure{\@dottedtocline{1}{1.5em}{2.3em}}
    \newcommand\listoftables{%
        \section*{\listtablename}%
          \@mkboth{%
              \MakeUppercase\listtablename}%
             {\MakeUppercase\listtablename}%
        \@starttoc{lot}%
        }
    \let\l@table\l@figure
    \newdimen\bibindent
    \setlength\bibindent{1.5em}
    \newenvironment{thebibliography}[1]
         {\section*{\refname}%
          \@mkboth{\MakeUppercase\refname}{\MakeUppercase\refname}%
          \list{\@biblabel{\@arabic\c@enumiv}}%
               {\settowidth\labelwidth{\@biblabel{#1}}%
                \leftmargin\labelwidth
                \advance\leftmargin\labelsep
                \@openbib@code
                \usecounter{enumiv}%
                \let\p@enumiv\@empty
                \renewcommand\theenumiv{\@arabic\c@enumiv}}%
          \sloppy
          \clubpenalty4000
          \@clubpenalty \clubpenalty
          \widowpenalty4000%
          \sfcode`\.\@m}
         {\def\@noitemerr
           {\@latex@warning{Empty `thebibliography' environment}}%
          \endlist}
    \newcommand\newblock{\hskip .11em\@plus.33em\@minus.07em}
    \let\@openbib@code\@empty
    \newenvironment{theindex}
                   {\if@twocolumn
                      \@restonecolfalse
                    \else
                      \@restonecoltrue
                    \fi
                    \twocolumn[\section*{\indexname}]%
                    \@mkboth{\MakeUppercase\indexname}%
                            {\MakeUppercase\indexname}%
                    \thispagestyle{plain}\parindent\z@
                    \parskip\z@ \@plus .3\p@\relax
                    \columnseprule \z@
                    \columnsep 35\p@
                    \let\item\@idxitem}
                   {\if@restonecol\onecolumn\else\clearpage\fi}
    \newcommand\@idxitem{\par\hangindent 40\p@}
    \newcommand\subitem{\@idxitem \hspace*{20\p@}}
    \newcommand\subsubitem{\@idxitem \hspace*{30\p@}}
    \newcommand\indexspace{\par \vskip 10\p@ \@plus5\p@ \@minus3\p@\relax}
    \renewcommand\footnoterule{%
      \kern-3\p@
      \hrule\@width.4\columnwidth
      \kern2.6\p@}
    \newcommand\@makefntext[1]{%
        \parindent 1em%
        \noindent
        \hb@xt@3pt{\hss\@makefnmark}#1}
    \newcommand\contentsname{Contents}
    \newcommand\listfigurename{List of Figures}
    \newcommand\listtablename{List of Tables}
    \newcommand\refname{References}
    \newcommand\indexname{Index}
    \newcommand\figurename{FIGURE}
    \newcommand\tablename{TABLE}
    \newcommand\partname{Part}
    \newcommand\appendixname{Appendix}
    \newcommand\abstractname{Abstract}
    \def\today{\ifcase\month\or
      January\or February\or March\or April\or May\or June\or
      July\or August\or September\or October\or November\or December\fi
      \space\number\day, %\number\year
    }
    \setlength\columnsep{10\p@}
    \setlength\columnseprule{0\p@}
    \pagestyle{plain}
    \pagenumbering{arabic}
    \if@twoside
    \else
      \raggedbottom
    \fi
    %\if@twocolumn
    %  \twocolumn
      \sloppy
      \flushbottom
      \raggedbottom
    %\else
      \onecolumn
    %\fi
    
    
    
    
    
    %%%%%%%%%%%Packages%%%%%%%%%%%%%
    %\usepackage{endnotes}%
    %\newif\ifEndNotes
    %\newcommand\queriesoff{\let\endnote\@gobble%
    %  \let\theendnotes\relax%
    %}
    %\newcommand\querieson{\EndNotestrue}
    
    %\querieson
    
    
    %\ifEndNotes
    %\else
    %  \let\endnote\@gobble
    %  \let\theendnotes\relax
    %\fi
    %\usepackage{upgreek}%
    \usepackage{mathspec}%Don't Change the package place
    \setmathrm{MinionPro-Regular}%
    \setmathfont(Digits,Latin){MinionPro-Regular}%
    \defaultfontfeatures{Ligatures={TeX,NoCommon}}%
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    \usepackage{booktabs}%
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%rulecolor changing%%%%%%%%%%%%%%%%%
    \usepackage{colortbl}%
    \arrayrulecolor{gray}%
    \usepackage{xcolor}%
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    \usepackage{graphics}%
    \usepackage{graphicx}%
    %\usepackage{ifthen}%
    \usepackage{amsmath,amssymb}%
    \usepackage[noblocks]{authblk}%
    \usepackage[colorlinks=true,allcolors=black]{hyperref}%
    %\usepackage{mdframed}%
    \usepackage{lineno}%
    \usepackage{color}%
    %\usepackage[numbers,sort&compress]{natbib}%%% 21-02-15
    \usepackage[numbers]{natbib}%
    \usepackage{xparse}%
    \usepackage{arrayjobx}%
    \usepackage{etoolbox}%
    %\usepackage[figuresright]{rotating}%
    \usepackage{url}%
    \urlstyle{same}%
    \usepackage{enumerate}% 
    \renewcommand{\labelitemi}{$\vcenter{\hbox{$\bullet$}}$}%
    \usepackage{xkeyval}%
    %\usepackage{environ}%
    \usepackage{marginnote}%
    \usepackage[english]{babel}%
    \usepackage{enumitem}
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    \newfontfamily{\HelveticaNeueLTStdBd}{HelveticaNeueLTStd-Bd}
    \newfontfamily{\HelveticaNeueLTStdBdIt}{HelveticaNeueLTStd-BdIt}
    \newfontfamily{\HelveticaNeueLTStdLt}{HelveticaNeueLTStd-Lt}
    \newfontfamily{\HelveticaNeueLTStdLtIt}{HelveticaNeueLTStd-LtIt}
    \newfontfamily{\HelveticaNeueLTStdMd}{HelveticaNeueLTStd-Md}
    \newfontfamily{\HelveticaNeueLTStdMdIt}{HelveticaNeueLTStd-MdIt}
    \newfontfamily{\MinionProBold}{MinionPro-Bold}
    \newfontfamily{\MinionProBoldIt}{MinionPro-BoldIt}
    \newfontfamily{\MinionProIt}{MinionPro-It}
    \newfontfamily{\MinionProRegular}{MinionPro-Regular}
    \newfontfamily{\MinionProSemiboldIt}{MinionPro-SemiboldIt}
    
    %%%%%%%%%%%%%%%%%%D column %%%%%%%%%%%%%%%%%
    \usepackage{dcolumn}
    \newcolumntype{d}[1]{D{.}{.}{#1}}
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    %%%%%%%%%%%%%%%%%%Linenumber%%%%%%%%%%%%%
    \usepackage{vruler}
    \patchcmd{\makevruler}
    {\tiny}
    {}
    {}
    {}
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    \newenvironment{supdata}[1][]{\medskip%
    \noindent{\HelveticaNeueLTStdBd\fontsize{7}{9.5}\selectfont #1~|}~\HelveticaNeueLTStdLt\fontsize{7}{9.5}\selectfont }
    {\par}
    \newenvironment{ack}[1][]{%
    \section*{#1}%
       }
    {}
    %%%%%%%%%%%%%%%%%%%%%%Figure Definitions%%%%%%%%%%%%%%%%%%%%%%
    \setlength\fboxsep{6\p@}
    \setlength\fboxrule{0.25pt}
    \def\figheadfont{\HelveticaNeueLTStdBd\fontsize{7}{9.5}\selectfont}
    \def\figcaptionfont{\HelveticaNeueLTStdLt\fontsize{7}{9.5}\selectfont}
    \def\figcapfont{\fontspec{HelveticaNeueLTStd-Lt}\fontsize{7}{9.5}\selectfont}
    \def\spdagger{\HelveticaNeueLTStdBd\fontsize{5.5}{6.5}\selectfont †}
    \def\sppdagger{\HelveticaNeueLTStdBd\fontsize{5.5}{6.5}\selectfont ‡}
    \def\metadagger{\protect\textsuperscript{\HelveticaNeueLTStdLtIt\fontsize{5.5}{6.5}\selectfont \char"2020}}
    \def\metaddagger{\protect\textsuperscript{\HelveticaNeueLTStdLtIt\fontsize{5.5}{6.5}\selectfont \char"2021}}
    \def\tableheadfont{\HelveticaNeueLTStdBd\fontsize{7}{9.5}\selectfont}
    \def\tablecaptionfont{\HelveticaNeueLTStdBd\fontsize{7}{9.5}\selectfont}
    \def\tablebodyfont{\HelveticaNeueLTStdLt\fontsize{7}{9.5}\selectfont}
    \def\tablefootfont{\HelveticaNeueLTStdLtIt\fontsize{6.5}{8.5}\selectfont}
    \newcommand{\colhead}[1]{\HelveticaNeueLTStdBd\fontsize{7}{9.5}\selectfont%
    \begin{tabular}{@{}c@{}}%
    #1\end{tabular}}
    \newcommand{\AuthName}[1]{{\HelveticaNeueLTStdLt\fontsize{7}{10}\selectfont #1\par}}
    
    \newcommand{\processfigure}[2]{\centering\fbox{\parbox{82mm}{\rightskip12\p@\centering#1\vspace*{-3.5\p@}\par\rightskip12\p@%
    \caption{#2}}}}
	\newcommand{\processdblfigure}[2]{\centering\fbox{\parbox{173.5mm}{\centering#1\vspace*{-3.5\p@}\par%
    \begin{multicols}{2}\caption{#2}
    \end{multicols}\vspace*{-12\p@}}}}
    
    \newcommand{\singledblfigure}[2]{\centering\fbox{\parbox{173.5mm}{\centering#1\vspace*{-3.5\p@}\par%
    \caption{#2}}}}
    
    \long\def\@makefigcaptiondouble#1#2{\vspace{\abovecaptionskip}%
    \figcaptionfont%
      \setbox\@tempboxa=\hbox{{{\figheadfont#1\ |\ }%
        \figcaptionfont#2}}%
      \ifdim\wd\@tempboxa>\hsize
      \MakeUppercase{\figheadfont{#1\ |\ }}%
    {\figheadfont #2}%
      \else
        \hbox to \hsize{\MakeUppercase{\figheadfont{#1\ |\ }}%
            \ignorespaces{\figheadfont #2}\hss}
      \fi}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%Table caption%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    \newcommand{\processtable}[3]{\renewcommand{\textbf}{\fontspec{HelveticaNeueLTStd-Bd}}\caption{#1}\par%
    {\tablebodyfont #2}\par%
    {\tablefootfont #3}}
    
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    \newcommand{\jnltype}[1]{%
      \def\jnllogo{\arrayx{jnllogo@aux}(#1)}%
      \def\jnlname{\arrayx{jnlname@aux}(#1)}%
      \def\jnlabbrname{\arrayx{jnlabbrname@aux}(#1)}%
      \def\artjnlname{\arrayx{artjnlname@aux}(#1)}%
      \jnlabbrevname{#1}%
      \def\jnlquerylink{\arrayx{jnlquerylink@aux}(#1)}%
      \def\jnlshtname{\arrayx{jnlshtname@aux}(#1)}%
      \def\jnledtbrdlink{\arrayx{jnledtbrdlink@aux}(#1)}%
      \def\jnlarchive{\arrayx{jnlarchive@aux}(#1)}%
    }
    
    
    \newcommand{\jnlabbrevname}[1]{%
      \protected@edef\@\jnlabbrevname{%
        \ifcase#1%
         \relax\noexpand\threecolumn@error@\jnlabbrevname{#1}\or%
    fnins\or 
    fnmol\or 
    fncel\or 
    fncir\or 
    fnana\or
    fnsys\or
    fnint\or
    fnbeh\or
    fnhum\or
    fncom\or
    fninf\or
    fnbot\or
    \or
    fnene\or
    fneng\or
    fngen\or
    fnmet\or
    fpsyt\or
    fneur\or
    fendo\or
    fgene\or
    fimmu\or
    fmicb\or
    fnagi\or
    fnent\or
    fnevo\or
    fnnes\or
    fnpro\or
    fnsyn\or
    fphar\or
    fphys\or
    fpls\or
    fpsyg\or
    fonc\or
    fcimb\or
    fped\or
    fpubh\or
    fmed\or
    fbioe\or
    fenrg\or
    fmats\or
    fsurg\or
    fnut\or
    frobt\or
    fcvm\or
    fvets\or
    fict\or
    fdigh\or
    fmech\or
    fpsyg\else
         \relax\noexpand\threecolumn@error@jnlabbrevname{#1}\fi
      }
    }
    
    
    \newarray\artjnlname@aux\readarray{artjnlname@aux}{%
    Frontiers in Neuroscience&Frontiers in Molecular Neuroscience&Frontiers in Cellular Neuroscience&Frontiers in Neural Circuits&Frontiers in Neuroanatomy&Frontiers in Systems Neuroscience&Frontiers in Integrative Neuroscience&Frontiers in Behavioral Neuroscience&Frontiers in Human Neuroscience&Frontiers in Computational Neuroscience&Frontiers in Neuroinformatics&Frontiers in Neurorobotics&Frontiers in Neuroscience and Society&Frontiers in Neuroenergetics&Frontiers in Neuroengineering&Frontiers in Neurogenomics&Frontiers in Neuromethods&Frontiers in Psychiatry&Frontiers in Neurology&Frontiers in Endocrinology&Frontiers in Genetics&Frontiers in Immunology&Frontiers in Microbiology&Frontiers in Aging Neuroscience&Frontiers in Enteric Neuroscience&Frontiers in Evolutionary Neuroscience&Frontiers in Neurogenesis&Frontiers in Neuroprosthetics&Frontiers in Synaptic Neuroscience&Frontiers in Pharmacology&Frontiers in Physiology&Frontiers in Plant Science&Frontiers in Psychology&Frontiers in Oncology&Frontiers in Cellular and Infection Microbiology&Frontiers in Pediatrics&Frontiers in Public Health&Frontiers in Medicine&Frontiers in Bioengineering and Biotechnology&Frontiers in Energy Research&Frontiers in Materials&Frontiers in Surgery&Frontiers in Nutrition&Frontiers in Robotics and AI&Frontiers in Cardiovascular Medicine&Frontiers in Veterinary Science&Frontiers in ICT&Frontiers in Digital Humanities&Frontiers in Mechanical Engineering&Frontiers in Psychology&&%
    }
    
    
    
    
    
    %%%%%%%%%%Numbered Sections%%%%%%%%%%%%%%%%%%
    \def\numbered{\setcounter{secnumdepth}{5}}%
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    \newcommand{\arttype}[1]{%
      \protected@edef\@arttype{%
        \ifcase#1%
         \relax\noexpand\threecolumn@error@arttype{#1}\or
                ORIGINAL RESEARCH ARTICLE\hss\or
                REVIEW ARTICLE\hss\or
                METHODS ARTICLE\hss\or
                HYPOTHESIS AND THEORY ARTICLE\hss\or
                OPINION ARTICLE\hss\or
                GENERAL COMMENTARY\hss\or
                REVIEWS IN MEDICINE\hss\else
         \relax\noexpand\threecolumn@error@arttype{#1}\fi
      }
    }
    
    \long\def\title{\@ifnextchar[{\short@title}{\@@title}}
    \def\short@title[#1]{\titlemark{\textcolor{gray}{#1}}\@@@title}
    \def\@@title#1{\authormark{#1}\@@@title{#1}}
    \long\def\@@@title#1{\gdef\@title{\hypersetup{pdftitle={#1}}#1}}
    \definecolor{querylinkcolor}{cmyk}{0.95,0.69,0.10,0}
    
    \newarray\jnlquerylink@aux\readarray{jnlquerylink@aux}{%
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}}&
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:engineering.production.office@frontiersin.org}{\textcolor{querylinkcolor}{engineering.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:engineering.production.office@frontiersin.org}{\textcolor{querylinkcolor}{engineering.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} &
    \href{mailto:engineering.production.office@frontiersin.org}{\textcolor{querylinkcolor}{engineering.production.office@frontiersin.org}} & 
    \href{mailto:health.production.office@frontiersin.org}{\textcolor{querylinkcolor}{health.production.office@frontiersin.org}} & 
    \href{mailto:engineering.production.office@frontiersin.org}{\textcolor{querylinkcolor}{engineering.production.office@frontiersin.org}}& 
    \href{mailto:engineering.production.office@frontiersin.org}{\textcolor{querylinkcolor}{engineering.production.office@frontiersin.org}}& &
    }
    
    \newarray\jnllogo@aux\readarray{jnllogo@aux}{%
    \href{http://www.frontiersin.org/Neuroscience/}{\XeTeXpdffile "01_fnins.pdf"}&\href{http://www.frontiersin.org/Molecular_Neuroscience/}{\XeTeXpdffile "02_fnmol.pdf"}&\href{http://www.frontiersin.org/Cellular_Neuroscience/}{\XeTeXpdffile "03_fncel.pdf"}&\href{http://www.frontiersin.org/Neural_Circuits/}{\XeTeXpdffile "04_fncir.pdf"}&\href{http://www.frontiersin.org/Neuroanatomy/}{\XeTeXpdffile "05_fnana.pdf"}&\href{http://www.frontiersin.org/Systems_Neuroscience/}{\XeTeXpdffile "06_fnsys.pdf"}&\href{http://www.frontiersin.org/Integrative_Neuroscience/}{\XeTeXpdffile "07_fnint.pdf"}&\href{http://www.frontiersin.org/Behavioral_Neuroscience/}{\XeTeXpdffile "08_fnbeh.pdf"}&\href{http://www.frontiersin.org/Human_Neuroscience/}{\XeTeXpdffile "09_fnhum.pdf"}&\href{http://www.frontiersin.org/Computational_Neuroscience/}{\XeTeXpdffile "10_fncom.pdf"}&\href{http://www.frontiersin.org/Neuroinformatics/}{\XeTeXpdffile "11_fninf.pdf"}&\href{http://www.frontiersin.org/Neurorobotics/}{\XeTeXpdffile "12_fnbot.pdf"}&{\errmessage{JNLTYPE-13 IS NOT DEFINED In THREECOLUMN TEMPLATE, Contact LaTeX Developer}}&\href{http://www.frontiersin.org/Neuroenergetics/}{\XeTeXpdffile "14_fnene.pdf"}&\href{http://www.frontiersin.org/Neuroengineering/}{\XeTeXpdffile "15_fneng.pdf"}&\href{http://www.frontiersin.org/Neurogenomics/}{\XeTeXpdffile "16_fngen.pdf"}&\href{http://www.frontiersin.org/Neuromethods/}{\XeTeXpdffile "17_fnmet.pdf"}&\href{http://www.frontiersin.org/Psychiatry/}{\XeTeXpdffile "18_fpsyt.pdf"}&\href{http://www.frontiersin.org/Neurology/}{\XeTeXpdffile "19_fneur.pdf"}&\href{http://www.frontiersin.org/Endocrinology/}{\XeTeXpdffile "20_fendo.pdf"}&\href{http://www.frontiersin.org/Genetics/}{\XeTeXpdffile "21_fgene.pdf}"&\href{http://www.frontiersin.org/Immunology/}{\XeTeXpdffile "22_fimmu.pdf"}&\href{http://www.frontiersin.org/Microbiology/}{\XeTeXpdffile "23_fmicb.pdf"}&\href{http://www.frontiersin.org/Aging_Neuroscience/}{\XeTeXpdffile "24_fnagi.pdf"}&\href{http://www.frontiersin.org/Enteric_Neuroscience/}{\XeTeXpdffile "25_fnent.pdf"}&\href{http://www.frontiersin.org/Evolutionary_Neuroscience/}{\XeTeXpdffile "26_fnevo.pdf"}&\href{http://www.frontiersin.org/Neurogenesis/}{\XeTeXpdffile "27_fnnes.pdf"}&\href{http://www.frontiersin.org/Neuroprosthetics/}{\XeTeXpdffile "28_fnpro.pdf"}&\href{http://www.frontiersin.org/Synaptic_Neuroscience/}{\XeTeXpdffile "29_fnsyn.pdf"}&\href{http://www.frontiersin.org/Pharmacology/}{\XeTeXpdffile "30_fphar.pdf"}&\href{http://www.frontiersin.org/Physiology/}{\XeTeXpdffile "31_fphys.pdf"}&\href{http://www.frontiersin.org/Plant_Science/}{\XeTeXpdffile "32_fpls.pdf"}&\href{http://www.frontiersin.org/Psychology/}{\XeTeXpdffile "33_fpsyg.pdf"}&\href{http://www.frontiersin.org/Oncology/}{\XeTeXpdffile "34_fonc.pdf"}&\href{http://www.frontiersin.org/cellular_and_infection_microbiology}{\XeTeXpdffile "35_fcimb.pdf"}&\href{http://www.frontiersin.org/Pediatrics}{\XeTeXpdffile "36_fped.pdf"}&\href{http://www.frontiersin.org/Public_Health}{\XeTeXpdffile "37_fpubh.pdf"}&\href{http://www.frontiersin.org/Medicine}{\XeTeXpdffile "38_fmed.pdf"}&\href{http://www.frontiersin.org/Bioengineering_and_Biotechnology}{\XeTeXpdffile "39_fbioe.pdf"}&\href{http://www.frontiersin.org/Energy_Research}{\XeTeXpdffile "40_fenrg.pdf"}&\href{http://www.frontiersin.org/Materials}{\XeTeXpdffile "41_fmats.pdf"}&\href{http://www.frontiersin.org/Surgery}{\XeTeXpdffile "42_fsurg.pdf"}&\href{http://www.frontiersin.org/Nutrition}{\XeTeXpdffile "43_fnut.pdf"}&\href{http://www.frontiersin.org/Robotics_and_AI}{\XeTeXpdffile "44_frobt.pdf"}&\href{http://www.frontiersin.org/Cardiovascular_Medicine}{\XeTeXpdffile "45_fcvm.pdf"}&\href{http://www.frontiersin.org/Veterinary_Science}{\XeTeXpdffile "46_fvets.pdf"}&\href{http://www.frontiersin.org/ICT}{\XeTeXpdffile "47_fict.pdf"}&\href{http://www.frontiersin.org/Digital_Humanities}{\XeTeXpdffile "48_fdigh.pdf"}&\href{http://www.frontiersin.org/Mechanical_Engineering}{\XeTeXpdffile "LOGO_Mechanical Engineering_1line.pdf"}&\href{http://www.frontiersin.org/Personality\_and\_Social\_Psychology}{\XeTeXpdffile "logos/fpsyg.pdf"}&&&%
    }
    
    \newarray\jnlname@aux\readarray{jnlname@aux}{%
    \href{http://www.frontiersin.org/Neuroscience/}{\textcolor{gray}{Frontiers in Neuroscience}}&\href{http://www.frontiersin.org/Molecular_Neuroscience/}{\textcolor{gray}{Frontiers in Molecular Neuroscience}}&\href{http://www.frontiersin.org/Cellular_Neuroscience/}{\textcolor{gray}{Frontiers in Cellular Neuroscience}}&\href{http://www.frontiersin.org/Neural_Circuits/}{\textcolor{gray}{Frontiers in Neural Circuits}}&\href{http://www.frontiersin.org/Neuroanatomy/}{\textcolor{gray}{Frontiers in Neuroanatomy}}&\href{http://www.frontiersin.org/System_Neuroscience/}{\textcolor{gray}{Frontiers in Systems Neuroscience}}&\href{http://www.frontiersin.org/Integrative_Neuroscience/}{\textcolor{gray}{Frontiers in Integrative Neuroscience}}&\href{http://www.frontiersin.org/Behavioral_Neuroscience/}{\textcolor{gray}{Frontiers in Behavioral Neuroscience}}&\href{http://www.frontiersin.org/Human_Neuroscience/}{\textcolor{gray}{Frontiers in Human Neuroscience}}&\href{http://www.frontiersin.org/Computational_Neuroscience/}{\textcolor{gray}{Frontiers in Computational Neuroscience}}&\href{http://www.frontiersin.org/Neuroinformatics/}{\textcolor{gray}{Frontiers in Neuroinformatics}}&\href{http://www.frontiersin.org/Neurorobotics/}{\textcolor{gray}{Frontiers in Neurorobotics}}&\href{}{\textcolor{gray}{Frontiers in Neuroscience and Society}}&\href{http://www.frontiersin.org/Neuroenergetics/}{\textcolor{gray}{Frontiers in Neuroenergetics}}&\href{http://www.frontiersin.org/Neuroengineering/}{\textcolor{gray}{Frontiers in Neuroengineering}}&\href{http://www.frontiersin.org/Neurogenomics/}{\textcolor{gray}{Frontiers in Neurogenomics}}&\href{http://www.frontiersin.org/Neuromethods/}{\textcolor{gray}{Frontiers in Neuromethods}}&\href{http://www.frontiersin.org/Psychiatry/}{\textcolor{gray}{Frontiers in Psychiatry}}&\href{http://www.frontiersin.org/Neurology/}{\textcolor{gray}{Frontiers in Neurology}}&\href{http://www.frontiersin.org/Endocrinology/}{\textcolor{gray}{Frontiers in Endocrinology}}&\href{http://www.frontiersin.org/Genetics/}{\textcolor{gray}{Frontiers in Genetics}}&\href{http://www.frontiersin.org/Immunology/}{\textcolor{gray}{Frontiers in Immunology}}&\href{http://www.frontiersin.org/Microbiology/}{\textcolor{gray}{Frontiers in Microbiology}}&\href{http://www.frontiersin.org/Aging_Neuroscience/}{\textcolor{gray}{Frontiers in Aging Neuroscience}}&\href{http://www.frontiersin.org/Enteric_Neuroscience/}{\textcolor{gray}{Frontiers in Enteric Neuroscience}}&\href{http://www.frontiersin.org/Evolutionary_Neuroscience/}{\textcolor{gray}{Frontiers in Evolutionary Neuroscience}}&\href{http://www.frontiersin.org/Neurogenesis/}{\textcolor{gray}{Frontiers in Neurogenesis}}&\href{http://www.frontiersin.org/Neuroprosthetics/}{\textcolor{gray}{Frontiers in Neuroprosthetics}}&\href{http://www.frontiersin.org/Synaptic_Neuroscience/}{\textcolor{gray}{Frontiers in Synaptic Neuroscience}}&\href{http://www.frontiersin.org/Pharmacology/}{\textcolor{gray}{Frontiers in Pharmacology}}&\href{http://www.frontiersin.org/Physiology/}{\textcolor{gray}{Frontiers in Physiology}}&\href{http://www.frontiersin.org/Plant_Science/}{\textcolor{gray}{Frontiers in Plant Science}}&\href{http://www.frontiersin.org/Psychology/}{\textcolor{gray}{Frontiers in Psychology}}&\href{http://www.frontiersin.org/Oncology/}{\textcolor{gray}{Frontiers in Oncology}}&\href{http://www.frontiersin.org/cellular_and_infection_microbiology}{\textcolor{gray}{Frontiers in Cellular and Infection Microbiology}}&\href{http://www.frontiersin.org/Pediatrics}{\textcolor{gray}{Frontiers in Pediatrics}}&\href{http://www.frontiersin.org/Public_Health}{\textcolor{gray}{Frontiers in Public Health}}&\href{http://www.frontiersin.org/Medicine}{\textcolor{gray}{Frontiers in Medicine}}&\href{http://www.frontiersin.org/Bioengineering_and_Biotechnology}{\textcolor{gray}{Frontiers in Bioengineering and Biotechnology}}&\href{http://www.frontiersin.org/Energy_Research}{\textcolor{gray}{Frontiers in Energy Research}}&\href{http://www.frontiersin.org/Materials}{\textcolor{gray}{Frontiers in Materials}}&\href{http://www.frontiersin.org/Surgery}{\textcolor{gray}{Frontiers in Surgery}}&\href{http://www.frontiersin.org/Nutrition}{\textcolor{gray}{Frontiers in Nutrition}}&\href{http://www.frontiersin.org/Robotics_and_AI}{\textcolor{gray}{Frontiers in Robotics and AI}}&\href{http://www.frontiersin.org/Cardiovascular_Medicine}{\textcolor{gray}{Frontiers in Cardiovascular Medicine}}&\href{http://www.frontiersin.org/Veterinary_Science}{\textcolor{gray}{Frontiers in Veterinary Science}}&\href{http://www.frontiersin.org/ICT}{\textcolor{gray}{Frontiers in ICT}}&\href{http://www.frontiersin.org/Digital_Humanities}{\textcolor{gray}{Frontiers in Digital Humanities}}&\href{http://www.frontiersin.org/Mechanical_Engineering}{\textcolor{gray}{Frontiers in Mechanical Engineering}}&\href{http://www.frontiersin.org/Personality_and_Social_Psychology}{\textcolor{gray}{Frontiers in Psychology}}&&%
    }
    
    \newarray\jnlabbrname@aux\readarray{jnlabbrname@aux}{%
    fnins&fnmol&fncel&fncir&fnana&fnsys&fnint&fnbeh&fnhum&fncom&fninf&fnbot&&fnene&fneng&fngen&fnmet&fpsyt&fneur&fendo&fgene&fimmu&fmicb&fnagi&fnent&fnevo&fnnes&fnpro&fnsyn&fphar&fphys&fpls&fpsyg&fonc&fcimb&fped&fpubh&fmed&fbioe&fenrg&fmats&fsurg&fnut&frobt&fcvm&fvets&fict&fdigh&fmech&fpsyg&&%
    }
    
    \newarray\jnlshtname@aux\readarray{jnlshtname@aux}{%
    Front. Neurosci.&Front. Mol. Neurosci.&Front. Cell. Neurosci.&Front. Neural Circuits&Front. Neuroanat.&Front. Syst. Neurosci.&Front. Integr. Neurosci.&Front. Behav. Neurosci.&Front. Hum. Neurosci.&Front. Comput. Neurosci.&Front. Neuroinform.&Front. Neurorobot.&&Front. Neuroenerg.&Front. Neuroeng.&Front. Neurogen.&Front. Neurom.&Front. Psychiatry&Front. Neur.&Front. Endocrin.&Front. Gene.&Front. Immun.&Front. Microbio.&Front. Ag. Neurosci.&Front. Ent. Neurosci.&Front. Evol. Neurosci.&Front. Neurogenesis&Front. Neuropro.&Front. Syn. Neurosci.&Front. Pharmacol.&Front. Physio.&Front. Plant Sci.&Front. Psychology&Front. Oncol.&Front. Cell. Inf. Microbio.&Front. Pediatr.&Front. Public Health&Front. Intern. Med.&Front. Bioeng. Biotechnol.&Front. Energy Res.&Front. Mat.&Front. Surg.&Front. Nutr.& Front. Robot. AI&Front. Cardiovasc. Med.&Front. Vet. Sci.& Front. ICT&Front. Digit. Humanit.&Front. Mech. Eng. &Front. Personality\_and\_Social\_Psychology&&%
    }
    
    \newarray\jnledtbrdlink@aux\readarray{jnledtbrdlink@aux}{%
    \href{http://www.frontiersin.org/Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Molecular_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Cellular_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Neural_Circuits/editorialboard}&\href{http://www.frontiersin.org/Neuroanatomy/editorialboard}&\href{http://www.frontiersin.org/System_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Integrative_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Behavioral_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Human_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Computational_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Neuroinformatics/editorialboard}&\href{http://www.frontiersin.org/Neurorobotics/editorialboard}&&\href{http://www.frontiersin.org/Neuroenergetics/editorialboard}&\href{http://www.frontiersin.org/Neuroengineering/editorialboard}&\href{http://www.frontiersin.org/Neurogenomics/editorialboard}&\href{http://www.frontiersin.org/Neuromethods/editorialboard}&\href{http://www.frontiersin.org/Psychiatry/editorialboard}&\href{http://www.frontiersin.org/Neurology/editorialboard}&\href{http://www.frontiersin.org/Endocrinology/editorialboard}&\href{http://www.frontiersin.org/Genetics/editorialboard}&\href{http://www.frontiersin.org/Immunology/editorialboard}&\href{http://www.frontiersin.org/Microbiology/editorialboard}&\href{http://www.frontiersin.org/Aging_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Enteric_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Evolutionary_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Neurogenesis/editorialboard}&\href{http://www.frontiersin.org/Neuroprosthetics/editorialboard}&\href{http://www.frontiersin.org/Synaptic_Neuroscience/editorialboard}&\href{http://www.frontiersin.org/Pharmacology/editorialboard}&\href{http://www.frontiersin.org/Physiology/editorialboard}&\href{http://www.frontiersin.org/Plant_Science/editorialboard}&\href{http://www.frontiersin.org/Psychology/editorialboard}&\href{http://www.frontiersin.org/Oncology/editorialboard}&\href{http://www.frontiersin.org/cellular_and_infection_microbiology/editorialboard}&\href{http://www.frontiersin.org/Pediatrics/editorialboard}&\href{http://www.frontiersin.org/Public_Health/editorialboard}&\href{http://www.frontiersin.org/Medicine/editorialboard}&\href{http://www.frontiersin.org/Bioengineering_and_Biotechnology/editorialboard}&\href{http://www.frontiersin.org/Energy_Research/editorialboard}&\href{http://www.frontiersin.org/Materials/editorialboard}&\href{http://www.frontiersin.org/Surgery/editorialboard}&\href{http://www.frontiersin.org/Nutrition/editorialboard}&\href{http://www.frontiersin.org/Robotics_and_AI/editorialboard}&\href{http://www.frontiersin.org/Cardiovascular_Medicine/editorialboard}&\href{http://www.frontiersin.org/Veterinary_Science/editorialboard}&\href{http://www.frontiersin.org/ICT/editorialboard}&\href{http://www.frontiersin.org/Digital_Humanities/editorialboard}&\href{http://www.frontiersin.org/Mechanical_Engineering/editorialboard}&\href{http://www.frontiersin.org/Personality\_and\_Social\_Psychology/editorialboard}&&&&%
    }
    
    
    \newarray\jnlarchive@aux\readarray{jnlarchive@aux}{%
    \href{http://www.frontiersin.org/Neuroscience/archive}&\href{http://www.frontiersin.org/Molecular_Neuroscience/archive}&\href{http://www.frontiersin.org/Cellular_Neuroscience/archive}&\href{http://www.frontiersin.org/Neural_Circuits/archive}&\href{http://www.frontiersin.org/Neuroanatomy/archive}&\href{http://www.frontiersin.org/System_Neuroscience/archive}&\href{http://www.frontiersin.org/Integrative_Neuroscience/archive}&\href{http://www.frontiersin.org/Behavioral_Neuroscience/archive}&\href{http://www.frontiersin.org/Human_Neuroscience/archive}&\href{http://www.frontiersin.org/Computational_Neuroscience/archive}&\href{http://www.frontiersin.org/Neuroinformatics/archive}&\href{http://www.frontiersin.org/Neurorobotics/archive}&&\href{http://www.frontiersin.org/Neuroenergetics/archive}&\href{http://www.frontiersin.org/Neuroengineering/archive} &\href{http://www.frontiersin.org/Neurogenomics/archive}&\href{http://www.frontiersin.org/Neuromethods/archive}&\href{http://www.frontiersin.org/Psychiatry/archive}&\href{http://www.frontiersin.org/Neurology/archive}&\href{http://www.frontiersin.org/Endocrinology/archive}&\href{http://www.frontiersin.org/Genetics/archive}&\href{http://www.frontiersin.org/Immunology/archive}&\href{http://www.frontiersin.org/Microbiology/archive}&\href{http://www.frontiersin.org/Aging_Neuroscience/archive}&\href{http://www.frontiersin.org/Enteric_Neuroscience/archive}&\href{http://www.frontiersin.org/Evolutionary_Neuroscience/archive}&\href{http://www.frontiersin.org/Neurogenesis/archive}&\href{http://www.frontiersin.org/Neuroprosthetics/archive}&\href{http://www.frontiersin.org/Synaptic_Neuroscience/archive}&\href{http://www.frontiersin.org/Pharmacology/archive}&\href{http://www.frontiersin.org/Physiology/archive}&\href{http://www.frontiersin.org/Plant_Science/archive}&\href{http://www.frontiersin.org/Psychology/archive}&\href{http://www.frontiersin.org/Oncology/archive}&\href{http://www.frontiersin.org/cellular_and_infection_microbiology/archive}&\href{http://www.frontiersin.org/Pediatrics/archive}&\href{http://www.frontiersin.org/Public_Health/archive}&\href{http://www.frontiersin.org/Medicine/archive}&\href{http://www.frontiersin.org/Bioengineering_and_Biotechnology/archive}&\href{http://www.frontiersin.org/Energy_Research/archive}&\href{http://www.frontiersin.org/Materials/archive}&\href{http://www.frontiersin.org/Surgery/archive}&\href{http://www.frontiersin.org/Nutrition/archive}&\href{http://www.frontiersin.org/Robotics_and_AI/archive}&\href{http://www.frontiersin.org/Cardiovascular_Medicine/archive}&\href{http://www.frontiersin.org/Veterinary_Science/archive}&\href{http://www.frontiersin.org/ICT/archive}&\href{http://www.frontiersin.org/Digital_Humanities/archive}&\href{http://www.frontiersin.org/Mechanical_Engineering/archive}&\href{http://www.frontiersin.org/Personality\_and\_Social\_Psychology/archive}&&&&%  
    }
    
    
    %%%%%%%%%%%%%%%%%%Pdf commands%%%%%%%%%%%%%%%
    \def\@mytitle{}
    \def\mytitle#1{\gdef\@mytitle{#1}}
    
    
    \def\@abstitle{}
    \def\abstitle#1{\gdef\@abstitle{#1}}
    
    \bibpunct[, ]{(}{)}{;}{a}{\color{gray},}{;}
    \hypersetup{%
    colorlinks,%
    linkcolor=black,%
    citecolor=gray,%
    bookmarks=true,
    bookmarksopen=true,%
    bookmarksnumbered=true,%
    pdftitle={\@mytitle},%
    pdfauthor={},%
    pdfkeywords={},%
    pdfsubject={}%
    }
    
    \def\corauthor{{\raisebox{-3pt}{\HelveticaNeueLTStdMdIt\fontsize{9}{11}\selectfont*}}}
    \def\titlefont{\HelveticaNeueLTStdBd\fontsize{21}{23}\selectfont}
    \def\abstractfont{\HelveticaNeueLTStdLt\fontsize{10}{14}\selectfont}
    \def\addressfont{\HelveticaNeueLTStdLtIt\fontsize{7}{10}\selectfont}
    \def\authorfont{\HelveticaNeueLTStdMdIt\fontsize{9}{11.5}\selectfont}
    \def\authornumberfont{\HelveticaNeueLTStdMdIt\fontsize{5.25}{7.25}\selectfont}
    \def\addressnumberfont{\HelveticaNeueLTStdLtIt\fontsize{4}{6}\selectfont}
    \def\editedbyfont{\HelveticaNeueLTStdBdIt\fontsize{7}{10}\selectfont}
    \def\editedaddressfont{\HelveticaNeueLTStdLtIt\fontsize{7}{10}\selectfont}
    \def\keywordfont{\HelveticaNeueLTStdBd\fontsize{7}{9.5}\selectfont}
    \def\metanotefont{\HelveticaNeueLTStdLtIt\fontsize{7}{10}\selectfont}
    \def\sectionfont{\HelveticaNeueLTStdBd\fontsize{12}{14}\selectfont}
    \def\subsectionfont{\HelveticaNeueLTStdBd\fontsize{10.5}{12.5}\selectfont}
    \def\subsubsectionfont{\HelveticaNeueLTStdMd\fontsize{10}{12}\selectfont}
    \def\paragraphfont{\MinionProBoldIt\fontsize{10.5}{12.5}\selectfont}
    \def\subparagraphfont{\MinionProSemiboldIt\fontsize{10}{12}\selectfont}
    \def\allevenfont{\fontsize{7}{9}\selectfont}
    \def\alloddfont{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont}
    \def\runevenfont{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont}
    \def\arunevenfont{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont}
    \def\runheadfont{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont}
    \def\toprunheadfont{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont}
    \def\articletypefont{\HelveticaNeueLTStdBd\fontsize{7}{9}\selectfont}
    \def\openingfont{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont}
    %%%%%%%%%Color Definitions%%%%%%%%%%%
    \definecolor{colorA}{cmyk}{1,0.70,0,0}
    \definecolor{gray}{cmyk}{0,0,0,0.70}
    %%%%%%%%%%%%%%%%%%Footer Design using subtype and subtype link%%%%%%%%%%%%
    
    
    
    \def\@jnlsubtype{}
    \def\jnlsubtype#1{\gdef\@jnlsubtype{#1}}
    
    \def\@jnlsubtypelink{}
    \def\jnlsubtypelink#1{\gdef\@jnlsubtypelink{#1}}
    
    \def\@DOI{}
    \def\DOI#1{\gdef\@DOI{#1}}
    
    \def\@DOIyear{}
    \def\DOIyear#1{\gdef\@DOIyear{#1}}
    
    %%%%%%%%%%%%%%%%%Conflict of Interest and Copyright%%%%%%%%%%%%%%%%
    \def\@conflict{}
    \def\conflict#1{\gdef\@conflict{\fontsize{7.5}{9.5}\selectfont\noindent\textbf{Conflict of Interest Statement:} #1}}
    
    \def\@copyrightauthor{}
    \def\copyrightauthor#1{\gdef\@copyrightauthor{#1}}
    
    \def\@copyright{}
    \def\copyright#1{\gdef\@copyright{\MinionProIt\fontsize{7.5}{9.5}\selectfont\noindent #1}}
    
    \copyright{Copyright~\textcopyright~\@DOIyear~\@copyrightauthor. This is an open-access article distributed under the terms of the \href{http://creativecommons.org/licenses/by/4.0/}{Creative Commons Attribution License (CC BY)}. The use, distribution or reproduction in other forums is permitted, provided the original author(s) or licensor are credited and that the original publication in this journal is cited, in accordance with accepted academic practice. No use, distribution or reproduction is permitted which does not comply with these terms.\vspace*{5pt}}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    \newcommand{\VOL}[1]{\gdef\@VOL{#1}}
    
    \def\@artseq{}
    \def\artseq#1{\gdef\@artseq{#1}}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%Editor and Reviewed Details%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    \let\@editor\@empty
    \newcommand{\editor}[1]{\protected@edef\@editor{\@editor #1\par}}
    
    \let\@reviewer\@empty
    \newcommand{\reviewer}[1]{\protected@edef\@reviewer{\@reviewer #1\par}}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    \def\@metanote{}
    \def\metanote#1{%
         \gdef\@metanote{\metanotefont\hfill  #1}}
    
    \newcommand\corhead{\editedbyfont\hfill *Correspondence:}
    \newcommand\specialtyhead{{\editedbyfont\hfill Specialty section:}}
    
    \def\@correspauthoroverride{}
    \def\correspauthoroverride#1{%
         \gdef\@correspauthoroverride{\corhead\newline%
           \editedaddressfont  #1}}
    
    \def\@presentaddressoverride{}
    \def\presentaddressoverride#1{%
         \gdef\@presentaddressoverride{{{\editedbyfont\hfill {\textsuperscript{\textit{\spdagger}}}Present address:}}\newline%
           \editedaddressfont  #1}}
    
    
    \def\@abstract{}
    \def\abstract#1{%
         \gdef\@abstract{\abstractfont #1}}
    
    \def\@keywords{}
    \def\keywords#1{%
         \gdef\@keywords{\keywordfont Keywords: #1\hypersetup{pdfkeywords={#1}}}}
    
    \def\@citationauthor{}
    \def\citationauthor#1{%
         \gdef\@citationauthor{#1}}
    
    \def\@authorrunning{}
    \def\authorrunning#1{%
         \gdef\@authorrunning{#1}}
    
    \def\@firstpara{}
    \def\firstpara#1{%
         \gdef\@firstpara{#1}}
    
    \def\@artcitation{}
    \def\artcitation#1{%
         \gdef\@artcitation{#1}}
    \newcommand\citehead{\HelveticaNeueLTStdBdIt\fontsize{7}{9}\selectfont Citation:}
    \artcitation{{\citehead}\break
    \HelveticaNeueLTStdLtIt\fontsize{7}{10}\selectfont {\@citationauthor} (\@DOIyear) {\@mytitle}}
    
    \def\@artsubmitted{}
    \def\artsubmitted#1{%
         \gdef\@artsubmitted{\HelveticaNeueLTStdLtIt\fontsize{7}{10}\selectfont #1}}
    
    %\newif\ifEndNotes
    %\def\queriesoff{\EndNotesfalse}
    %\def\querieson{\EndNotestrue}
    
    %\querieson
    %%\queriesoff Un-comment out to suppress the end notes
    
    %\makeatletter
    %\ifEndNotes
    %\else
    %  \let\endnote\@gobble
    %  \let\theendnotes\relax
    %\fi
    %makeatother
    
    %\newif\ifjnlsubtype
    
    %\def\jnlsubtypeoff{\jnlsubtypefalse}
    %\def\jnlsubtypeon{\jnlsubtypetrue}
    
    %\ifjnlsubtype
    %\jnlsubtypeon
    \artsubmitted{\specialtyhead\newline%
    This article was submitted to Personality\_and\_Social\_Psychology, a~section of the journal \artjnlname}
    %\else
    %\jnlsubtypeoff
    %\let\jnlsubtype\@gobble
    %\let\jnlsubtype\relax
    %\artsubmitted{This article was submitted to , a~section of the journal \artjnlname}
    %\fi
    
    %\if\relax\jnlsubtype\relax
    %\artsubmitted{This article was submitted to , a~section of the journal \artjnlname}
    %\else
    %\global\artsubmitted{\specialtyhead\newline%
    %This article was submitted to \@jnlsubtype, a~section of the journal \artjnlname}
    %\fi
    
    
    \newcommand{\addrline}[1]{#1}
    
    \newcommand{\customizeref}[3]{\hyperref[#1]{\textbf{#2\ref{#1}}}{\textbf{\hyperref[#1]{#3}}}}
    
    
    \def\corauthor{\raisebox{-5pt}{\HelveticaNeueLTStdMdIt\fontsize{9}{11}\selectfont *}}
    
    %Ex CMD:\setmainfont[Ligatures=TeX,Scale=0.95]{Some Nice Font}
    \setmainfont{MinionPro-Regular}
    
    %\usepackage{mathspec}
    %\setmathfont{MinionPro-Regular}
    
    
    %\usepackage[MnSymbol]{mathspec}
    %\setmathsfont(Digits,Latin){MinionPro-Regular}
    
    %vrulerfont \fontspec{MinionPro-Regular}\fontsize{9.5}{11.5}\selectfont
    
    %Old Font Changing Requirement
    \renewcommand\normalsize{%
    \@setfontsize\normalsize{9.5pt}{11.5pt}% 
      \abovedisplayskip 8pt plus2pt minus4pt%
      \belowdisplayskip\abovedisplayskip%
      \abovedisplayshortskip \z@ plus3pt%
      \belowdisplayshortskip 5pt plus3pt minus3pt%
      \let\@listi\@listI%
    }
    
    
    
    \def\ps@allpage{%
    \def\@evenhead{%
    \vbox{\vskip6.5pt%
    \hbox to\textwidth{\toprunheadfont\textcolor{gray}{\@authorrunning}\hfill{\rightmark}\strut}\vskip4.7pt
    \textcolor{gray}{\hrule width\textwidth height0.25pt}
    }
    }%
    \def\@evenfoot{\vbox to 11.72pt{\vskip14pt%
    \textcolor{gray}{\hrule width\textwidth height0.25pt}\vspace{5.9pt}%
    \hbox to\textwidth{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont\jnlname~\textcolor{gray}{|}~\href{http://www.frontiersin.org}{\textcolor{gray}{www.frontiersin.org}}\hfil{\jnlarchive{\textcolor{gray}{\onlinemonth}~\textcolor{gray}{\onlineyear}~\textcolor{gray}{|}~\textcolor{gray}{Volume}~\textcolor{gray}{\@VOL}~\textcolor{gray}{|}~\textcolor{gray}{Article}~\textcolor{gray}{\@artseq}}}}\vspace*{-21pt}%
    \hbox to \textwidth{\hfil\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont\textcolor{gray}{ \fontspec{HelveticaNeueLTStd-Bd}{\thepage}}\hfil}%
    }
    }%
    \def\@oddfoot{\vbox to 11.72pt{\vskip14pt%
    \textcolor{gray}{\hrule width\textwidth height0.25pt}\vspace{5.9pt}%
    \hbox to\textwidth{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont\jnlname~\textcolor{gray}{|}~\href{http://www.frontiersin.org}{\textcolor{gray}{www.frontiersin.org}}\hfil{\jnlarchive{\textcolor{gray}{\onlinemonth}~\textcolor{gray}{\onlineyear}~\textcolor{gray}{|}~\textcolor{gray}{Volume}~\textcolor{gray}{\@VOL}~\textcolor{gray}{|}~\textcolor{gray}{Article}~\textcolor{gray}{\@artseq}}}}\vspace*{-21pt}%
    \hbox to \textwidth{\hfil\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont\textcolor{gray}{\fontspec{HelveticaNeueLTStd-Bd}{\thepage}}\hfil}%
    }
    }
    \def\@oddhead{%
    \vbox{\vskip6.5pt%
    \hbox to\textwidth{\toprunheadfont\textcolor{gray}{\@authorrunning}\hfill{\rightmark}\strut}\vskip4.7pt
    \textcolor{gray}{\hrule width\textwidth height0.25pt}
    }
        \let\@mkboth\@gobbletwo
    %    \let\sectionmark\@gobble
    %    \let\subsectionmark\@gobble
        }
      \def\titlemark##1{\gdef\rightmark{##1}}%
      \def\authormark##1{\gdef\leftmark{##1}}%
        }
    
    \pagestyle{allpage}
    
    \def\ps@opening{\let\@mkboth\@gobbletwo
    \def\@oddfoot{\vbox to 11.72pt{\vskip14pt%
    \textcolor{gray}{\hrule width\textwidth height0.25pt}\vspace{5.9pt}%
    \hbox to\textwidth{\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont\jnlname~\textcolor{gray}{|}~\href{http://www.frontiersin.org}{\textcolor{gray}{www.frontiersin.org}}\hfil{\jnlarchive{\textcolor{gray}{\onlinemonth}~\textcolor{gray}{\onlineyear}~\textcolor{gray}{|}~\textcolor{gray}{Volume}~\textcolor{gray}{\@VOL}~\textcolor{gray}{|}~\textcolor{gray}{Article}~\textcolor{gray}{\@artseq}}}}\vspace*{-21pt}%
    \hbox to \textwidth{\hfil\HelveticaNeueLTStdLt\fontsize{7}{9}\selectfont\textcolor{gray}{\fontspec{HelveticaNeueLTStd-Bd}{\thepage}}\hfil}%
    }
    }%
    \def\@oddhead{\vbox{\vskip5.5pt%
    {\vfill%
    \hbox to \textwidth{\hspace*{-2.2pt}\includegraphics[scale=0.25]{logos/fpsyg.eps}\hfill\strut}\vskip4pt%
    \jnledtbrdlink{
    \hbox to \textwidth{\hss\hbox{\vbox to 0pt{\vskip-29pt\hbox{{\textcolor{black}{\color{gray}\articletypefont\@arttype}}}}}}\vskip2pt%
    {\hbox to \textwidth{\hss\hbox{\vbox to 0pt{\vskip-23pt\hbox{{\textcolor{black}{\color{gray}\openingfont published:~\onlineday\ \onlinemonth\ \onlineyear}}}}}}}\vskip-4pt
    \hbox to \textwidth{\hss\hbox{\vbox to 0pt{\vskip-12.3pt\hbox{{\textcolor{black}{\color{gray}\openingfont doi:~10.3389/{\jnlabbrname}.{\onlineyear}.{\@DOI}}}}}}}
    }
    }
    \vskip-1pt\textcolor{gray}{\hrule width\textwidth height0.25pt}
    }
    }
    }
    
    
    %%%%%%%%%%%%This macro should be hide single author name and affiliation is appeared%%%%%%%%
    \usepackage{letltxmacro}%%%%%%%%%%%%Address Counter Macro
    \newcounter{affiliations}%%%
    \LetLtxMacro{\authblkaddress}{\address}%%%%%
    \renewcommand{\address}[1]{%
    \stepcounter{affiliations}%
    \authblkaddress[\theaffiliations]{#1}}%
    %\renewcommand{\address}[1]{%
    %\ifnum\c@address>1
    % \authblkaddress[$\relax$]{#1}%
    %\else\ifnum\c@address>1
    %  \stepcounter{affiliations}%
    %  \authblkaddress[\theaffiliations]{#1}%
    %\fi\fi}
    
    
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    \newcommand\editedhead{\editedbyfont Edited by:\break}
    \newcommand\reviewerhead{\editedbyfont Reviewed by:\break}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%Command key Sections%%%%%%%%%%%%%%%%%%%%
    
    \define@key{authorinfo}{aff}{%
    \def\VetriKVMacroAff{#1}%
    }%
    
    
    \define@key{authorinfo}{coraddress}{%
    \def\VetriKVMacroCorAddress{#1}%
    }%
    
    \define@key{authorinfo}{email}{%
    \def\VetriKVMacroEmail{#1}%
    }%
    
    
    \let\@email\@empty
    \newcommand{\email}[1]{\protected@edef\@email{ \href{mailto:#1}{#1}}}
    
    
    \define@key{authorinfo}{presaddress}{%
    \def\VetriKVMacroPresentAddress{#1}%
    }%
    
    
    
    %\define@key{authorinfo}{email}{%
    %\def\VetriKVMacroEmail{e-mail: \href{mailto:#1}{#1}}%
    %}%
    
    
    \let\OriginalAuthor\author
    
    \RenewDocumentCommand{\author}{+O{}+m}{%
    \setkeys{authorinfo}{#1}%
    \ifdef{\VetriKVMacroAff}{\hypersetup{pdfauthor={#2}}%
      \OriginalAuthor[\VetriKVMacroAff]{#2}%
    }{%
      \OriginalAuthor{#2}% 
    }%
    \ifdef{\VetriKVMacroCorAddress}{%
      \correspauthoroverride{\VetriKVMacroCorAddress}%
    }{%
    }
    \ifdef{\VetriKVMacroPresentAddress}{%
      \presentaddressoverride{\VetriKVMacroPresentAddress}%
    }{%
    }%
    \ifdef{\VetriKVMacroEmail}{%
      \email{\VetriKVMacroEmail}%
    }{%
    }%
    \undef\VetriKVMacroAff%
    }% End of RenewDocumentCommand.
    
    
    \def\@maketitle{%
      \newpage
      \vspace*{-2pt}
      \null
    \vbox to \textheight{
    \vbox to 656pt{\vfill%
        \hbox to 114.45pt{\hfill%
        \begin{minipage}[b]{114.45pt}%
        \begin{flushright}%
        {\protect\href{https://creativecommons.org/licenses/by/4.0/}{\protect\includegraphics{logos/OpenAccessLogo.eps}}\par}%
        \vspace{9.5pt}%
        {\editedaddressfont\hfill{\editedhead}\@editor\par}%
        \ifdim\lastskip>0.0pt\unskip\fi\vskip 3.5pt%
        {\editedaddressfont\hfill{\reviewerhead}\@reviewer}%
        \ifdim\lastskip>0pt\unskip\fi\vskip 3.5pt%
        {\@correspauthoroverride\par%
        \@email\par}%
        \ifdim\lastskip>0pt\unskip\fi\vskip 3.5\p@%
        {\@presentaddressoverride\par%
        \@email\par}%
        \ifdim\lastskip>0pt\unskip\fi\vskip 3.5\p@%
        {\@metanote\par}%
        \ifdim\lastskip>0pt\unskip\fi\vskip 13\p@%
        {\@artsubmitted\par}
        \ifdim\lastskip>0pt\unskip\fi\vskip 3.5pt%  
       {\HelveticaNeueLTStdLtIt\fontsize{7}{10}\selectfont\rcdday~\rcdmonth~\rcdyear\par    \pubday~\pubmonth~\pubyear\par%
        \accday~\accmonth~\accyear\par%
       {\HelveticaNeueLTStdBdIt\fontsize{7}{10}\selectfont Published:}~\onlineday~\onlinemonth~\onlineyear\par}%
        \ifdim\lastskip>0pt\unskip\fi\vskip 3.5pt%
        {\@artcitation\par}%    
        \end{flushright}%   
        \end{minipage}}}%
    \hspace*{132.5pt}%
    \vbox to \textheight{\vspace*{-48.5pc}%
            \hbox to 375.49pt{\hfill%
    \begin{minipage}[b]{375.49pt}% 
      \let \footnote \thanks%
        {\raggedright\titlefont\href{http://www.frontiersin.org/Journal/10.3389/\@\jnlabbrevname.\@DOIyear.\@DOI/abstract}{\@title}\par}%
        \vskip 0.5em%
        {\large%
          \lineskip .36em%
          \begin{tabular}[t]{l}%
            \raggedright\@author%
          \end{tabular}\par}%
        \vskip 0.45em%
        {\@abstitle\@abstract\hypersetup{pdfkeywords={\@abstitle}}\par}%
        \vskip 1em%
        {\@keywords\par}%
        \vskip 1em%
        {\@firstpara\par}%
       \end{minipage}}}}%
      \par\setcounter{page}{1}\thispagestyle{opening}%
      \vskip 8.5em\twocolumn}
    
    
    %\newenvironment{ack}[1]{\section*{#1}
    %}{}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    %%%%%%%%%%%%%%%%%%%bibsec%%%%%%%%%%%%%%%%%%
    
    %%%%%%%%%%%%%%%%%%%%%Reference xml supported commands%%%%%%%%%%%%%%
    \def\etal{et~al}%
    \def\snm{}%
    \def\fnm{}%
    \def\year{}%
    \def\arttitle{}%
    \def\source{}%
    \def\vol{}%
    \def\issue{}%
    \def\page{}%
    \def\doi#1{doi:\href{http://dx.doi.org/#1}{#1}}%
    \def\PMID#1{%
    %#1
    }%
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%Numbered and author year references%%%%%%%%%%%%%%%%%%%%
    
    \def\numberedbib{\setcitestyle{numbers}}%
    \renewcommand\@biblabel[1]{\mbox{#1}.\hskip-4.5pt}%   
    
    
    \renewenvironment{thebibliography}[1]{%
    \vspace*{1.25pt}
    \bibpreamble\MinionProRegular\fontsize{7.5}{9.5}\selectfont\list
    {\@biblabel{\arabic{NAT02@ctr}}}{%
         \setlength{\labelsep}{1em}%
         \@bibsetup{#1}%
         \setcounter{NAT@ctr}{0}}%
         \ifNAT@openbib
         \def\newblock{\par}
        \else
          \def\newblock{\hskip .11em \@plus.33em \@minus.07em}%
        \fi
        \sloppy\clubpenalty4000\widowpenalty4000
        \sfcode`\.=1000\relax
        \let\citeN\cite \let\shortcite\cite
        \let\citeasnoun\cite
        \setlength\itemsep{\z@}}
    {
    \def\@noitemerr{%
      \PackageWarning{natbib}%
         {Empty `thebibliography' environment}}%
      \endlist\vskip-\lastskip\par%
    \medskip%
    {\hspace*{-10pt}\parbox[!t]{\columnwidth}{\@conflict}\par}%
    \medskip%
    {\hspace*{-10pt}\parbox[!t]{\columnwidth}{\@copyright}\par}}
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    \AtBeginDocument{%
    {\pagestyle{empty}%
    \onecolumn%
    \unsetvruler%
    %\theendnotes\clearpage%
    }%
    \twocolumn%
    }
    \usepackage{showframe}
    
    \setvruler[10.2pt][1][1][3][1][557pt][557pt][10pt][\textheight]%
    \setvruler[10.2pt][1][1][3][1][30pt][30pt][10pt][\textheight]%
    
    \def\final{\unsetvruler%
    \queriesoff}%
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    %% colortbl support
    
    \hyphenation{figure figures Figure Figures table tables Table Tables section sections Section Sections}%
    
    %%%%%%
    % Set badness and tolerance
    \vbadness=10000%
    \tolerance=9999%
    
    % Don't allow consecutive hyphens and hyphens at the bottom of the page.
    \doublehyphendemerits 100000%
    \doublehyphendemerits 640000%
    \finalhyphendemerits  1000000%
    \hyphenpenalty1000
    \tolerance9999
    \lefthyphenmin=3%
    
    % Disallow widows and orphans
    \clubpenalty 10000%
    \widowpenalty 10000%
    
    % Disable page breaks before equations, allow pagebreaks after
    % equations and discourage widow lines before equations.
    \displaywidowpenalty 500%
    \predisplaypenalty   10000%
    \postdisplaypenalty  0%
    
    \newcommand\auquery[1]{#1}
    \def\leftquery#1#2#3{{\marginpar{\vspace*{-6.2pt}\vspace*{#1}\hspace*{#2}{\fboxsep1pt\fbox{\textcolor{red}{\fontsize{7.5}{7.5}\selectfont#3}}}}}}
    %\let\auquery\endnote
    
    \frenchspacing%Single word spacing controlled constantly
    
    % Allow breaking the page in the middle of a paragraph
    \interlinepenalty 0%
    
    % Disallow breaking the page after a hyphenated line
    \brokenpenalty 10000%
    
    % Hyphenation; don't split words into less than three characters
    %\lefthyphenmin=3%
    %\righthyphenmin=3%
    \setlength\parskip{0pt}%
    
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    
    %%%Set Trim Size%%%%%
    
    
    \usepackage[%
    a4paper,%
    paperwidth=597.5pt,%
    paperheight=782.4pt,%
    textwidth=7.018in,%
    textheight=9.08in,%
    columnsep=13.7pt,%
    top=2.06cm,%
    bottom=2.35cm,%
    left=45.28pt,%
    right=45.28pt,%
    headheight=10.63pt,%
    headsep=26.25pt,%
    footskip=21pt,%
    ]{geometry}
    
    %\setlength{\paperheight}{782.4pt}%782.4pt(779.5pt)
    %\setlength{\paperwidth}{597.5pt}%597.5pt(595.3pt)
    %\setlength{\textheight}{664pt}
    %\setlength{\textwidth}{505.5pt}
    %\setlength\evensidemargin{46pt}
    %\addtolength{\evensidemargin}{-1in}
    %\addtolength{\oddsidemargin}{-1in}
    %\setlength\oddsidemargin{\evensidemargin}
    %\setlength\columnsep{11\p@}
    %\setlength\topmargin{-51\p@}
    %\setlength\footskip{30\p@}
    
    \makeatletter
    \newenvironment{tablehere}[1]
    {\noindent\begin{minipage}{#1}\parindent\z@\def\@captype{table}\let\@makecaption\@tablecaption}
    {\end{minipage}}
    \newenvironment{figurehere}[1]
    {\noindent\begin{minipage}{#1}\parindent\z@\def\@captype{figure}}
    {\end{minipage}}
    \makeatother
    
    \usepackage{xifthen,array}
    \makeatletter
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%% Queries %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    %
    \newwrite\@qrynotes
    \newif\if@qrynotesopen \global\@qrynotesopenfalse
    
    \def\@openqrynotes{\immediate\openout\@qrynotes=\jobname\thechapqry.qry\relax
    %\immediate\write\@auxout{\string\newif\csname if\jobname\roman{chapqry}\endcsname}
    %\expandafter\csname if\jobname\roman{chapqry}\endcsname%
    %\expandafter\global\csname jobname\roman{chapqry}false\endcsname
          \global\@qrynotesopentrue}
    
    \long\def\Protected@immwrite#1#2{%
          \begingroup%
           \let\protect\@unexpandable@protect%
           \edef\reserved@a{\immediate\write#1{\fontsize{12bp}{14bp}\selectfont #2}}%
           \reserved@a%
          \endgroup}%
    
    \newif\ifbwf@querymark\bwf@querymarktrue
    \newif\ifprintquery\global\printqueryfalse
    
    \newcounter{chapqry}
    \setcounter{chapqry}{0}
    
    \newcounter{qrycount}[chapqry]
    
    \newdimen\querywidth
    
    \querywidth=3pc
    
    \def\defaultcondition{TRUE}
    
    \DeclareRobustCommand\AQ{\unskip\@ifnextchar[{\@AQtbmove}{\@AQprint}}%
    
    \def\@AQtbmove[#1]#2{\@ifnextchar[{\@AQtbmoveprint[#1]{#2}}{\@AQtbmoveprint[#1]{#2}[0pt]}}%
    
    \def\@AQtbmoveprint[#1]#2[#3]{\ifbwf@querymark\stepcounter{qrycount}%
    \if@qrynotesopen \else  \@openqrynotes \fi%
     \Protected@immwrite\@qrynotes{\string AQ\the\c@qrycount & #2 &\protect\\ }%
    % \ifnum\thechapqry=\thechapqry
    %\expandafter\if\csname jobname\roman{chapqry}\endcsname
    \expandafter\ifx\csname processcount\roman{chapqry}\endcsname\defaultcondition%
     \AQ@margtext[#1]{AQ\the\c@qrycount}[#3]%
    \fi\fi}%
    
    \def\@AQprint#1{\@ifnextchar[{\@AQprintquery{#1}}{\@AQprintquery{#1}[0pt]}}%
    
    \def\@AQprintquery#1[#2]{\ifbwf@querymark\stepcounter{qrycount}%
    \if@qrynotesopen \else  \@openqrynotes \fi%
     \Protected@immwrite\@qrynotes{\string AQ\the\c@qrycount & #1 &\protect\\ }%
    % \expandafter\if\csname jobname\roman{chapqry}\endcsname
    \expandafter\ifx\csname processcount\roman{chapqry}\endcsname\defaultcondition%
     {\AQ@margtext[0pt]{AQ\the\c@qrycount}[#2]}%
    \fi\fi}%
    
    \newif\if@rightcolumnquery\global\@rightcolumnqueryfalse%
    
    \def\RAQ#1{\global\@rightcolumnquerytrue\AQ{#1}}
    
    \newdimen\lastpagetotaldim
    \def\AQ@margtext[#1]#2[#3]{%
      \ifmmode%
      \else%
        \setbox\@tempboxa=\vbox to 0pt{\vskip-9pt\vskip#1%
        \if@rightcolumnquery%
        \global\@rightcolumnqueryfalse%
          \hbox to \hsize{\hfill\hskip#3\rlap{\hbox to \querywidth{\hskip12pt\reset@font\normalcolor\normalsize #2\hfill}}}%
        \else%
          \ifdim\pagetotal=\lastpagetotaldim{\protect\par\vskip12pt}\else\fi%
          \global\lastpagetotaldim=\pagetotal%
          \hbox to \hsize{\hskip#3\llap{\hbox to \querywidth{\reset@font\normalcolor\normalsize #2\hfill}}\hfill}%
        \fi}%
        \dp\@tempboxa\z@%
        \ifvmode%
          \@tempdima=\prevdepth%
          \nointerlineskip\box\@tempboxa\nobreak%
          \prevdepth=\@tempdima%
        \else%
          \vadjust{\box\@tempboxa\nobreak}\space%
        \fi%
      \fi\penalty10000%
    }
    \newbox\qrylabelbox
    
    \newenvironment{qrylist}[1][\relax]{%
    \list{}%
    {\setbox\qrylabelbox\hbox{\normalsize#1.}
    \labelsep8pt
    \labelwidth\wd\qrylabelbox%
    \leftmargin\labelwidth%
    \advance\leftmargin\labelsep%
    \rightmargin\z@%
    \def\makelabel##1{\hbox to \labelwidth{\hfill##1.}}}%
    }%
    {\endlist}
    
    \def\notesname{\fontfamily{ptm}\fontsize{17bp}{17bp}\selectfont\bfseries Author Query Form}%
    \def\qnoteheading{%
    \clearpage%
    \gdef\watermarktext{}
    \addtocounter{page}{-1}%
    \pagestyle{empty}
    \ifthenelse{\isodd{\thepage}}{\addtocounter{page}{-1}}{\addtocounter{page}{-1}}
    \vspace*{-7pc}
    %\lineno@off%
    %\ifbwf@rmblankpage
    %\addtocounter{page}{-1}%
    %\setcounter{curpage}{\arabic{page}}
    %\else
    %\setcounter{curpage}{\arabic{page}}
    %\ifodd\thecurpage
    %\addtocounter{curpage}{-1}%
    %\fi%
    \fi%
    \centerline{\notesname}%
    \rule{\textwidth}{1pt}\vskip2\baselineskip\noindent{\fontfamily{ptm}\fontsize{12bp}{12bp}\selectfont\bfseries Journal: Statistics in Medicine\par\addvspace{10.5\p@}Article: STA\par\addvspace{20pt}}\fontfamily{ptm}\fontsize{12bp}{14bp}\selectfont Dear Author,\par\addvspace{2pc} During the copyediting of your paper,the following queries arose. Please respond to these by annotating your proofs with the necessary changes/additions.\begin{itemize}
    \item If you intend to annotate your proof electronically, please refer to the E-annotation guidelines.
    \item If you intend to annotate your proof by means of hard-copy mark-up, please refer to the proofmark-upsymbols guidelines.
    If manually writing corrections on your proof and returning it by fax, do not write
    too close to the edge of the paper. Please remember that illegible mark-ups may delay publication
    \end{itemize}
    Whether you opt for hard-copy or electronic annotation of your proofs,
    were commend that you provide additional clarification of answers to queries
    by entering your answers on the query sheet, in addition to the textmark-up.
    }
    
    \RequirePackage{longtable}
    \def\printquery{
    \immediate\write\@auxout{\string\gdef\expandafter\string\csname processcount\roman{chapqry}\endcsname{TRUE}}\printquerytrue\ifprintquery%\immediate\write\@auxout{\expandafter\string\expandafter\global\csname\jobname\roman{chapqry}true\endcsname}%
    \immediate\closeout\@qrynotes \global\@qrynotesopenfalse%
    %%
    \ifnum\c@qrycount>0
    \qnoteheading
    \vspace*{2pc}
    
    \begin{longtable}{@{}|l|>{\raggedright\parindent0pt}p{.6\textwidth}|p{.175\textwidth}|@{}}\hline%
    \textbf{Query No.} & \textbf{Query} & \textbf{Remark}\\
    \endfirsthead
    \hline
    \textbf{Query No.} & \textbf{Query} & \textbf{Remark}\\
    \hline
    \endhead
    \hline
    \multicolumn{1}{c}{}& \multicolumn{1}{c}{}& \multicolumn{1}{r}{\hfill (Continued..)}\\
    \endfoot
    \hline
    \endlastfoot
    \hline
    \input{\jobname\thechapqry.qry}
    \hline
    \end{longtable}
    \fi\par\addvspace{24\p@}
    %\fi%\lineno@on\setcounter{lastpage}{\arabic{page}}\addtocounter{lastpage}{-\c@curpage}
    }%
    
    %
    %%%%%%%%%% Author query part end %%%%%%%%%%%%
    \makeatother
    
    
    
    \ExplSyntaxOn
    \NewDocumentCommand{\received}{ >{ \SplitArgument { 2 } { / } } m }
     {
      \received_main:nnn #1
     }
    \cs_new_protected:Npn \received_main:nnn #1 #2 #3
     {
      \cs_gset:Npn \rcdday {{\HelveticaNeueLTStdBdIt\fontsize{7}{9}\selectfont Received:}\ #1 }
      \cs_gset:Npx \rcdmonth { \prop_get:Nn \g_received_months_prop { #2 } }
      \cs_gset:Npn \rcdyear { #3 }
     }
    \prop_new:N \g_received_months_prop
    \prop_gput:Nnn \g_received_months_prop { 01 } { January }
    \prop_gput:Nnn \g_received_months_prop { 02 } { February }
    \prop_gput:Nnn \g_received_months_prop { 03 } { March }
    \prop_gput:Nnn \g_received_months_prop { 04 } { April }
    \prop_gput:Nnn \g_received_months_prop { 05 } { May }
    \prop_gput:Nnn \g_received_months_prop { 06 } { June }
    \prop_gput:Nnn \g_received_months_prop { 07 } { July}
    \prop_gput:Nnn \g_received_months_prop { 08 } { August }
    \prop_gput:Nnn \g_received_months_prop { 09 } { September }
    \prop_gput:Nnn \g_received_months_prop { 10 } { October }
    \prop_gput:Nnn \g_received_months_prop { 11 } { November }
    \prop_gput:Nnn \g_received_months_prop { 12 } { December }
    
    \def\pubday{}%
    \def\pubmonth{}%
    \def\pubyear{}%
    \NewDocumentCommand{\pubdate}{ >{ \SplitArgument { 2 } { / } } m }
     {
      \pubdate_main:nnn #1
     }
    \cs_new_protected:Npn \pubdate_main:nnn #1 #2 #3
     {
      \cs_gset:Npn \pubday {{\HelveticaNeueLTStdBdIt\fontsize{7}{9}\selectfont Paper~pending~published:}\ #1 }
      \cs_gset:Npx \pubmonth { \prop_get:Nn \g_pubdate_months_prop { #2 } }
      \cs_gset:Npn \pubyear { #3 }
     }
    \prop_new:N \g_pubdate_months_prop
    \prop_gput:Nnn \g_pubdate_months_prop { 01 } { January }
    \prop_gput:Nnn \g_pubdate_months_prop { 02 } { February }
    \prop_gput:Nnn \g_pubdate_months_prop { 03 } { March }
    \prop_gput:Nnn \g_pubdate_months_prop { 04 } { April }
    \prop_gput:Nnn \g_pubdate_months_prop { 05 } { May }
    \prop_gput:Nnn \g_pubdate_months_prop { 06 } { June }
    \prop_gput:Nnn \g_pubdate_months_prop { 07 } { July }
    \prop_gput:Nnn \g_pubdate_months_prop { 08 } { August }
    \prop_gput:Nnn \g_pubdate_months_prop { 09 } { September }
    \prop_gput:Nnn \g_pubdate_months_prop { 10 } { October }
    \prop_gput:Nnn \g_pubdate_months_prop { 11 } { November }
    \prop_gput:Nnn \g_pubdate_months_prop { 12 } { December }
    
    
    \NewDocumentCommand{\accepted}{ >{ \SplitArgument { 2 } { / } } m }
     {
      \accepted_main:nnn #1
     }
    \cs_new_protected:Npn \accepted_main:nnn #1 #2 #3
     {
      \cs_gset:Npn \accday {{\HelveticaNeueLTStdBdIt\fontsize{7}{9}\selectfont Accepted:}\ #1 }
      \cs_gset:Npx \accmonth { \prop_get:Nn \g_accepted_months_prop { #2 } }
      \cs_gset:Npn \accyear { #3 }
     }
    \prop_new:N \g_accepted_months_prop
    \prop_gput:Nnn \g_accepted_months_prop { 01 } { January }
    \prop_gput:Nnn \g_accepted_months_prop { 02 } { February }
    \prop_gput:Nnn \g_accepted_months_prop { 03 } { March }
    \prop_gput:Nnn \g_accepted_months_prop { 04 } { April }
    \prop_gput:Nnn \g_accepted_months_prop { 05 } { May }
    \prop_gput:Nnn \g_accepted_months_prop { 06 } { June }
    \prop_gput:Nnn \g_accepted_months_prop { 07 } { July }
    \prop_gput:Nnn \g_accepted_months_prop { 08 } { August }
    \prop_gput:Nnn \g_accepted_months_prop { 09 } { September }
    \prop_gput:Nnn \g_accepted_months_prop { 10 } { October }
    \prop_gput:Nnn \g_accepted_months_prop { 11 } { November }
    \prop_gput:Nnn \g_accepted_months_prop { 12 } { December }
    
    \NewDocumentCommand{\online}{ >{ \SplitArgument { 2 } { / } } m }
     {
      \online_main:nnn #1
     }
    \cs_new_protected:Npn \online_main:nnn #1 #2 #3
     {
      \cs_gset:Npn \onlineday { #1 }
      \cs_gset:Npx \onlinemonth { \prop_get:Nn \g_online_months_prop { #2 } }
      \cs_gset:Npn \onlineyear { #3 }
     }
    \prop_new:N \g_online_months_prop
    \prop_gput:Nnn \g_online_months_prop { 01 } { January }
    \prop_gput:Nnn \g_online_months_prop { 02 } { February }
    \prop_gput:Nnn \g_online_months_prop { 03 } { March }
    \prop_gput:Nnn \g_online_months_prop { 04 } { April }
    \prop_gput:Nnn \g_online_months_prop { 05 } { May }
    \prop_gput:Nnn \g_online_months_prop { 06 } { June }
    \prop_gput:Nnn \g_online_months_prop { 07 } { July }
    \prop_gput:Nnn \g_online_months_prop { 08 } { August }
    \prop_gput:Nnn \g_online_months_prop { 09 } { September }
    \prop_gput:Nnn \g_online_months_prop { 10 } { October }
    \prop_gput:Nnn \g_online_months_prop { 11 } { November }
    \prop_gput:Nnn \g_online_months_prop { 12 } { December }
    \ExplSyntaxOff
    \raggedbottom
    %%%%26/02/15
    
    \def\headsub#1{{$_{\smash{\hbox{\fontsize{8}{8}\selectfont\fontspec{HelveticaNeueLTStd-Bd}{#1}}}}$}}
    
    \DeclareFontFamily{U}{mtt}{}
    \DeclareFontShape{U}{mtt}{m}{up}{<->mtgu}{}
    \DeclareFontShape{U}{mtt}{b}{up}{<->mtgub}{}
    \DeclareSymbolFont{upgreek}{U}{mtt}{m}{up}
    \SetSymbolFont{upgreek}{normal}{U}{mtt}{m}{up}
    \SetSymbolFont{upgreek}{bold}{U}{mtt}{b}{up}
    \DeclareMathSymbol{\reta}{\mathalpha}{upgreek}{'041}
    \DeclareMathSymbol{\rtheta}{\mathalpha}{upgreek}{'042}
    \DeclareMathSymbol{\rphi}{\mathalpha}{upgreek}{'043}
    \DeclareMathSymbol{\rchi}{\mathalpha}{upgreek}{'044}
    \DeclareMathSymbol{\rpsi}{\mathalpha}{upgreek}{'045}
    \DeclareMathSymbol{\romega}{\mathalpha}{upgreek}{'046}
    \DeclareMathSymbol{\rTheta}{\mathalpha}{upgreek}{'047}
    \DeclareMathSymbol{\rPhi}{\mathalpha}{upgreek}{'050}
    \DeclareMathSymbol{\rPsi}{\mathalpha}{upgreek}{'051}
    \DeclareMathSymbol{\rvarepsilon}{\mathalpha}{upgreek}{'053}
    \DeclareMathSymbol{\rvartheta}{\mathalpha}{upgreek}{'054}
    \DeclareMathSymbol{\rvarpi}{\mathalpha}{upgreek}{'055}
    \DeclareMathSymbol{\rvarrho}{\mathalpha}{upgreek}{'056}
    \DeclareMathSymbol{\rvarsigma}{\mathalpha}{upgreek}{'057}
    \DeclareMathSymbol{\rvarphi}{\mathalpha}{upgreek}{'060}
    \DeclareMathSymbol{\rvarkappa}{\mathalpha}{upgreek}{'061}
    \DeclareMathSymbol{\rOmega}{\mathalpha}{upgreek}{'062}
    \DeclareMathSymbol{\rDelta}{\mathalpha}{upgreek}{'104}
    \DeclareMathSymbol{\rGamma}{\mathalpha}{upgreek}{'107}
    \DeclareMathSymbol{\rLambda}{\mathalpha}{upgreek}{'114}
    \DeclareMathSymbol{\rPi}{\mathalpha}{upgreek}{'120}
    \DeclareMathSymbol{\rSigma}{\mathalpha}{upgreek}{'123}
    \DeclareMathSymbol{\rUpsilon}{\mathalpha}{upgreek}{'125}
    \DeclareMathSymbol{\rXi}{\mathalpha}{upgreek}{'130}
    \DeclareMathSymbol{\ralpha}{\mathalpha}{upgreek}{'141}
    \DeclareMathSymbol{\rbeta}{\mathalpha}{upgreek}{'142}
    \DeclareMathSymbol{\rdelta}{\mathalpha}{upgreek}{'144}
    \DeclareMathSymbol{\repsilon}{\mathalpha}{upgreek}{'145}
    \DeclareMathSymbol{\rgamma}{\mathalpha}{upgreek}{'147}
    \DeclareMathSymbol{\riota}{\mathalpha}{upgreek}{'151}
    \DeclareMathSymbol{\rkappa}{\mathalpha}{upgreek}{'153}
    \DeclareMathSymbol{\rlambda}{\mathalpha}{upgreek}{'154}
    \DeclareMathSymbol{\rmu}{\mathalpha}{upgreek}{'155}
    \DeclareMathSymbol{\rnu}{\mathalpha}{upgreek}{'156}
    \DeclareMathSymbol{\rpi}{\mathalpha}{upgreek}{'160}
    \DeclareMathSymbol{\rrho}{\mathalpha}{upgreek}{'162}
    \DeclareMathSymbol{\rsigma}{\mathalpha}{upgreek}{'163}
    \DeclareMathSymbol{\rtau}{\mathalpha}{upgreek}{'164}
    \DeclareMathSymbol{\rnu}{\mathalpha}{upgreek}{'165}
    \DeclareMathSymbol{\rxi}{\mathalpha}{upgreek}{'170}
    \DeclareMathSymbol{\rzeta}{\mathalpha}{upgreek}{'172}
    \DeclareSymbolFont{upgreekbold}{U}{mtt}{b}{up}
    \SetSymbolFont{upgreekbold}{normal}{U}{mtt}{b}{up}
    \SetSymbolFont{upgreekbold}{bold}{U}{mtt}{b}{up}
    \DeclareMathSymbol{\boeta}{\mathalpha}{upgreekbold}{'041}
    \DeclareMathSymbol{\btheta}{\mathalpha}{upgreekbold}{'042}
    \DeclareMathSymbol{\bphi}{\mathalpha}{upgreekbold}{'043}
    \DeclareMathSymbol{\bchi}{\mathalpha}{upgreekbold}{'044}
    \DeclareMathSymbol{\bpsi}{\mathalpha}{upgreekbold}{'045}
    \DeclareMathSymbol{\bomega}{\mathalpha}{upgreekbold}{'046}
    \DeclareMathSymbol{\bTheta}{\mathalpha}{upgreekbold}{'047}
    \DeclareMathSymbol{\bPhi}{\mathalpha}{upgreekbold}{'050}
    \DeclareMathSymbol{\bPsi}{\mathalpha}{upgreekbold}{'051}
    \DeclareMathSymbol{\bvarepsilon}{\mathalpha}{upgreekbold}{'053}
    \DeclareMathSymbol{\bvartheta}{\mathalpha}{upgreekbold}{'054}
    \DeclareMathSymbol{\bvarpi}{\mathalpha}{upgreekbold}{'055}
    \DeclareMathSymbol{\bvarrho}{\mathalpha}{upgreekbold}{'056}
    \DeclareMathSymbol{\bvarsigma}{\mathalpha}{upgreekbold}{'057}
    \DeclareMathSymbol{\bvarphi}{\mathalpha}{upgreekbold}{'060}
    \DeclareMathSymbol{\bvarkappa}{\mathalpha}{upgreekbold}{'061}
    \DeclareMathSymbol{\bOmega}{\mathalpha}{upgreekbold}{'062}
    \DeclareMathSymbol{\bDelta}{\mathalpha}{upgreekbold}{'104}
    \DeclareMathSymbol{\bGamma}{\mathalpha}{upgreekbold}{'107}
    \DeclareMathSymbol{\bLambda}{\mathalpha}{upgreekbold}{'114}
    \DeclareMathSymbol{\bPi}{\mathalpha}{upgreekbold}{'120}
    \DeclareMathSymbol{\bSigma}{\mathalpha}{upgreekbold}{'123}
    \DeclareMathSymbol{\bUpsilon}{\mathalpha}{upgreekbold}{'125}
    \DeclareMathSymbol{\bXi}{\mathalpha}{upgreekbold}{'130}
    \DeclareMathSymbol{\balpha}{\mathalpha}{upgreekbold}{'141}
    \DeclareMathSymbol{\bbeta}{\mathalpha}{upgreekbold}{'142}
    \DeclareMathSymbol{\bdelta}{\mathalpha}{upgreekbold}{'144}
    \DeclareMathSymbol{\bepsilon}{\mathalpha}{upgreekbold}{'145}
    \DeclareMathSymbol{\bgamma}{\mathalpha}{upgreekbold}{'147}
    \DeclareMathSymbol{\biota}{\mathalpha}{upgreekbold}{'151}
    \DeclareMathSymbol{\bkappa}{\mathalpha}{upgreekbold}{'153}
    \DeclareMathSymbol{\blambda}{\mathalpha}{upgreekbold}{'154}
    \DeclareMathSymbol{\bmu}{\mathalpha}{upgreekbold}{'155}
    \DeclareMathSymbol{\bnu}{\mathalpha}{upgreekbold}{'156}
    \DeclareMathSymbol{\bpi}{\mathalpha}{upgreekbold}{'160}
    \DeclareMathSymbol{\brho}{\mathalpha}{upgreekbold}{'162}
    \DeclareMathSymbol{\bsigma}{\mathalpha}{upgreekbold}{'163}
    \DeclareMathSymbol{\btau}{\mathalpha}{upgreekbold}{'164}
    \DeclareMathSymbol{\bnu}{\mathalpha}{upgreekbold}{'165}
    \DeclareMathSymbol{\bxi}{\mathalpha}{upgreekbold}{'170}
    \DeclareMathSymbol{\bzeta}{\mathalpha}{upgreekbold}{'172}
    
    \endinput
    
    %\usepackage{floatrow}%
    
    \DeclareNewFloatType{Box}{%
      placement=htbp,
      fileext=lob}
    
    \floatsetup[Box]{%
      style=BOXED,%
      capposition=top,%
      justification=justified}
    
    %\usepackage{mdframed,capt-of}
    \usepackage[export]{adjustbox}
      
    \newenvironment{BOX}[2][htbp]{%
      \begin{Box}[#1]
        \ifx\relax#2\relax\else\caption{\textbf{#2}}\fi
    }{\end{Box}}
    
    \newenvironment{BOX*}[2][htbp]{%
      \begin{Box*}[#1]
        \ifx\relax#2\relax\else\caption{\textbf{#2}}\fi
    }{\end{Box*}}
    
    \output\expandafter{\the\output\floatfix}
    
    
