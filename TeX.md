## Grundlegdene Elemente ##

Absatz um zb. 0.25 cm 
	\\[0.25cm]

## Bild auf voller Breite eibinden ##

	\begin{figure}[!htbp]
		\centering
		\includegraphics[width=0.2\textwidth]{img/<name>.png}
	\end{figure}
	\captionsetup{belowskip=0pt}

## Bild mit links verlaufendem Text ##

	\begin{wrapfigure}{r}{0.3\textwidth}
		\vspace{-10pt}
		\includegraphics[width=0.3\textwidth]{img/<name>.jpg}
		\caption{<Beschreibung>}
		\quelle {\cite{bibid}}
		\label{fig:<short>}
	\end{wrapfigure}

## Tabelle ##

	\begin{table}[!htbp]
		\centering
		\caption{Regelung für Fahrstraßen nach dem Verschlussplanprinzip}
		\label{tab:vsp}
		\begin{tabular}{|l|r|c|c|c|c|c|c|c|c|c|c|c|c|c|}
			\multicolumn{2}{r|}{\textbf{Fahrstraße} \hspace{0.75cm} \rule[0cm]{0cm}{7cm} \begin{rotate}{90}\textbf{Feldelemente}\end{rotate}} & \hspace{0.1cm} \begin{rotate}{90}{[...] (Durchrutschweg) in Gl.424}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Fahrstraße von Gl.402 nach BBG}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Fahrstraße von Gl.424 nach BBG}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Feldblock nach BBG}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Gleisfreimeldegruppe Gl. 973}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Gleisfreimeldegruppe Gl. 401}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Gleisfreimeldegruppe Gl. 403}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Weichengruppe 226}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Weichengruppe 227}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Weichengruppe 230 / 231}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Weichengruppe 233 / 235}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{Bahnübergangssicherung(sanlage)}\end{rotate} & \hspace{0.1cm} \begin{rotate}{90}{[...]}\end{rotate} \\ \hline
			\multicolumn{2}{c|}{von BBG nach Gl.401} & ~ & - & ~ & ~ & ~ & O & ~ & - & ~ & - & - & 1 & ~ \\ \hline
			\multicolumn{2}{c|}{von Gl.403 nach BBG} & - & - & - & O & O & ~ & ~ & ~ & - & - & - & 1 & ~ \\ \hline
			\multicolumn{2}{c|}{von BBG nach Gl.403} & - & - & - & ~ & ~ & ~ & O & ~ & - & + & - & 1 & ~ \\ \hline
			\multicolumn{2}{c|}{von Gl.401 nach BBG} & ~ & - & - & O & O & ~ & ~ & - & ~ & - & + & 1 & ~ \\ \hline
			\multicolumn{2}{c}{\rule[0cm]{2cm}{0cm}[...]\rule[0cm]{2cm}{0cm}} & \multicolumn{13}{c}{~} \\ 
		\end{tabular}
	\end{table} 

## Grafiken ##

	\begin{figure}[!htbp]
		\centering
		\setlength{\unitlength}{1cm}
		\begin{picture}(16,3)
			\put(0,2){\framebox (15.9,0.9){Leit- und Sicherungstechnik}}
			\put(0,0){\framebox (2.9,1.9){Leittechnik}}
			\put(3,1){\framebox (12.9,0.9){EBO: (Eisenbahn-) Sicherungstechnik}}
			\put(3,0){\framebox (3.9,0.9){Fahrwegsicherung}}
			\put(7,0){\framebox (3.9,0.9){Zugbeeinflussung}}
			\put(11,0){\framebox (4.9,0.9){Bahnübergangssicherung}}
		\end{picture}
		\caption{Gliederung der Teilbereich der \acl{LsT}}
		\quelle{\cite[S. 2]{2022.SdS}}
		\label{fig:Lst_begriff}
	\end{figure}

## Überschrift & Inhaltsverzeichnis ##
Standard Kapitel
	\section{<Titel>}
	\subsection{<Titel>}
	\subsubsection{<Titel>}

Titel ohne einfügen im Inhaltsverzeichnis
	\section*{<Titel>}
	\subsection*{<Titel>}
	\subsubsection*{<Titel>}

Zwanghaftes einfügen ohne Numierung
	\addcontentsline{toc}{section}{<Titel>}

## Quellen ##
Standard mäßig
	'\cite[<Zusatz>]{<bibte>}'

Fußzeilenzitate
	'\footcite[<Zusatz>]{<bibte>}'

Auf der Hauptseite folgendes Einfügen, dann kann der Tag "\quelle" an allen elemnete einen Quellenverweis erzeugen:
	% Erzeugt eine Quelle am Bild
	\newcommand*{\quelle}{%
		\raggedleft
			\footnotesize Quelle:
	}

Der zu nutzende Verweis:
	'\quelle{\cite[<Zusatz>]{<bibte>}}'