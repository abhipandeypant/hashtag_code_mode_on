# hashtag_code_mode_on
SAS Practice -Exercise -01   
Hello every one today we are going to start leran SAS , which we using for data analysis purpose . 

/* How to create datset from exixting datset */
data xx;
set sashelp.cars;
run;

/* how to create multiple datset from datset */
data xx yy;
set sashelp.cars;
run;

/* how to print dataset as per your requirement--if --we can not use with proc stmt */
proc print data=xx;
where Make="Audi";
run;

/*vertical subsetting- keep and drop as a dataset option and keep and drop as a statement*/
/*keep and drop as dataset option*/

data v_subset(Keep =Make Model);/*less efficient filtering on target dataset*/
set sashelp.cars ;
run;

data v_subset2(drop=Make Model);/*less efficient filtering on target dataset*/
set sashelp.cars;
run;

data v_subset;
set sashelp.cars (Keep =Make Model);/*More efficient filtering on source dataset*/
run;

data v_subset2;
set sashelp.cars(drop=Make Model);/*More efficient filtering on source dataset*/
run;

/*horizontal subsetting*/

/*if statement* Post buffer it applies filter after copy data --less efficient*/
/*--if we can not with the newly created var bcs if do filter from the target dataset */

data if_db;
set abhi_lib.admit;
if Sex="M";
run;

/* where statement* pre buffer it applies filter before copy data ---more efficient*/
/*--where we can not with the newly created var bcs where do filter from the source dataset */

data where_a;
set abhi_lib.admit;
where Sex="F";
run;
