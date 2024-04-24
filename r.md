#R
##Kopfzeilen##
	#set working directory
	setwd(dirname(rstudioapi::getSourceEditorContext()$path))
	#database connection
	con <- dbConnect(RPostgres::Postgres(), dbname = db,
	                 host = host, port = port,
	                 user = user, password = pw)
	sql <- "select * from <Tabelle>;"
	df <- dbGetQuery(con, sql)
	#Anzeigen der Daten
	tibble::glimpse(df)

##Plots##
	ggplot(head(df), aes(reorder(-sum_ew,ags),sum_ew)) +
	  geom_col() +
	  geom_text(aes(label = format(sum_ew, big.mark = ".", scientific = FALSE)), vjust = -0.5, size=5) +
	  labs(title="Gemeinden in NRW mit den meisten Einwohnern nach Zensus 2011",x="Gemeinde", y="Einwohner") +
	  scale_x_discrete(expand = c(0,0), label=c('Köln','Düsseldorf','Dortmund','Essen','Duisburg','Bochum')) +
	  scale_y_continuous(labels = function(x) format(x, big.mark = ".", decimal.mark = ',', scientific = FALSE),
	                     expand = c(0,0), limits = c(0,1080000)) +
	  theme_minimal_hgrid() + 
	  theme_bw()
	  #theme(plot.title = element_text(size = 20, face = "bold", hjust = 0.5, vjust = 2))

##Weiteres##
	#Grafik Speichern
	png(file="<name.png>", width=210, height=148, units="mm", res=300)
		<Plot>
	dev.off()