# udemy_project_portilla;


DESCRIPTION:

In this repository, you will find the following two analyses; the determinant factors of 

(i)"Bribery incidence", 

(ii)"Research and Development" 

for the countries

2) Data; World Bank Enterprise Survey

some 

python;

#turing year columns into rows

	df = pd.melt(df, id_vars=['Country Name','Country Code','Series Name'], value_vars=df.columns[4:])

#pivotting data frame

	df = pd.pivot_table(df, values='value',index=['Country Name', 'Country Code', 'variable'],
	               columns='Series Name', dropna=True ).reset_index().rename_axis(None, axis=1)

#eliminating those countries with more than one observation

	df_c = df.copy()
	for i in set(df['Country Name'].values):
	    num = len(df[df['Country Name']==i])
	    if num > 1:
	        df_c = df_c[df_c['Country Name'] != i]
	        d = df[df['Country Name']==i].tail(1)
	        df_c = pd.concat([df_c, d])


r;

#turing year columns into rows

	df <- melt(df,id.vars=c('country','code','serie'), measure.vars =c(colnames(df)[5:length(colnames(df))]))

#pivotting data frame

	df_p <- dcast(df, country + code + year ~ serie, value.var="value", fun.aggregate=sum)

#eliminating those countries with more than one observation

	for (i in unique(df_m$country)){
	  d <- subset(df_m, subset = df_m$country == i)
	  if (nrow(d) > 1){
	    d <- tail(d, 1)
	    df_m <- subset(df_m, subset = df_m$country != i)
	    df_m <- rbind(df_m, d) 
	  }
	}
	df_m

Some insights:

1. In terms of Bribery Analysis;

	1.1 Vandalism, proportion of investment financed by a bank, the degree meeting with tax official are determinant factors for Bribery incidence as (percent of firms experiencing at least one bribe payment request in lineal regression model while having a saving account, financing by a bank, and having own web site are determinant factors in Random Forest Model

	1.2 Based on the beginning point, data is divided into 5 or 7 clusters. 

2. Regarding R & D Analysis;

	2.1 foreign partner participation, international certification, and training in a firm are important factors for the percent of firms that spend on R&D in a country in a linear regression model. On the other hand, female participation is also a determinant input in the Random Forest model. 

	2.2 After dividing data into 5 or 7 clusters, it seems that location also plays an important role to differentiate countries based on explanatory variables


