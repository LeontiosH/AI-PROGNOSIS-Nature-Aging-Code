# AI-PROGNOSIS-Nature-Aging-Code

AI-driven motor and cognitive decline digital assessment for Parkinson’s disease: a systematic review and meta-analysis

Sofia B. Dias1, Ghada Alhussein2,3, Beatriz Alves2, Margherita Fabbri4, Olivier Rascol4, Maria-Luisa Almarcha-Menargues5, Mónica Kurtis Urra5, Nikos Grammalidis6, Kosmas Dimitropoulos6, Stelios Hadjidimitriou7, Leontios J. Hadjileontiadis7,3, on behalf of the AI-PROGNOSIS Consortium†

submitted to Nature Aging
(please cite it accordingly)
************************************************
1.  System requirements

Requires STATA Version 17.0, Midas, Metandi modules

The software was tested on STATA Version 17.0SE on a ThinkPad X1 Lenovo x64-based PC, X1 Carbon 6th, Intel(R) Core(TM) i7-8550U CPU@1.80GH, 1992 Mhz, 4 Cores, 8 Logical Processors, OS Microsoft Windows 11 Pro

There is no need for any non-standard hardware

2. Installation guide
   * Instructions
     
     First install the STATA Verison 17.0 from https://www.stata.com/support/download-install/

     Then install the MIDAS and METANDI modules as follows:
     ssc install midas, replace
     ssc install metandi, replace
     
   * Typical online install time on a "normal" desktop computer
     
     STATA 17.0 installation 5-12 mins
     
     Midas, Metandi modules 5 secs
     
3. Demo
   
   *Instructions to run on data
   
First copy the content of the theMIDAS-ADO_CodeByLeontios.txt file and replace the whole code of STATA midas.ado file. This will allow the estimation of additional parameters that are not exported by the current version of the midas.ado
Then, to run the whole analysis, use the following .do files that run as batches:

batchLeontiosMain.do
batchLeontiosMetaREG.do
batchLeontiosSubGROUP.do

They call, accordingly, the following .do analysis files

AI_PROGNOSIS_Main.do
AI_PROGNOSIS_MetaRegressionV1.do
AI_PROGNOSIS_SubGrouping_FINAL

Save these .do codes in your code folder. In the current batch codes the following directory is used:

C:/NatAgingPaper/MainFigsDataDo

If you want to change it, open the batch files and edit the directory to the one you want.
Select the directory of your data and update the datafolder in the command window.
Hence, to do this without changing the .do file write in the command window:

********* for the main figures

global codefolder "C:/NatAgingPaper/MainFigsDataDo" * here are the one used by me
global datafolder "C:/NatAgingPaper/FinallyUsedRev1-USETHIS/ManusciptFigs" * here are the one used by me
cd C:/NatAgingPaper/FinallyUsedRev1-USETHIS/ManusciptFigs * here are the one used by me
do "C:/NatAgingPaper/MainFigsDataDo/batchLeontiosMain.do" * here are the one used by me

************ for the suppl figures

global codefolder "C:/NatAgingPaper/MainFigsDataDo" * here are the one used by me
global datafolder "C:\NatAgingPaper\FinallyUsedRev1-USETHIS\SupplFigs" * here are the one used by me
cd C:\NatAgingPaper\FinallyUsedRev1-USETHIS\SupplFigs * here are the one used by me
do "C:/NatAgingPaper/MainFigsDataDo/batchLeontiosMainFigs.do" * here are the one used by me

************ for the metaregression analysis

global codefolder "C:/NatAgingPaper/MainFigsDataDo" * here are the one used by me
global datafolder "C:\NatAgingPaper\FinallyUsedRev1-USETHIS\MetaRegression" * here are the one used by me
cd C:\NatAgingPaper\FinallyUsedRev1-USETHIS\MetaRegression * here are the one used by me
do "C:/NatAgingPaper/MainFigsDataDo/batchLeontiosMetaREG.do" * here are the one used by me
 
************ for the subgrouping testing analysis

global codefolder "C:/NatAgingPaper/MainFigsDataDo" * here are the one used by me
global datafolder "C:\NatAgingPaper\FinallyUsedRev1-USETHIS\SubGrouping" * here are the one used by me
cd C:\NatAgingPaper\FinallyUsedRev1-USETHIS\SubGrouping * here are the one used by me
do "C:/NatAgingPaper/MainFigsDataDo/batchLeontiosSubGROUP.do" * here are the one used by me

   * Expected output
     
The batch files run for every .csv that has the contingency tables and exist in the datafolder. Output folders are automatically created, with all related material (.gph, .png, .xlsx).

Note that in the AI_PROGNOSIS_SubGrouping_FINAL, the covariates explored in the paper were used as names. To avoid any error, update with the names of your covariates, accordingly. Here is the current setting of the covariates' name and short name, that should be edited according to your covariates' names and short names.
-Short names (your mapping)
    if "`v'"=="sensorplacement"        local shortname "sg_spl"
    else if ("`v'"=="mldl")            local shortname "sg_mldl"
    else if ("`v'"=="medsonoff")       local shortname "sg_med"
    else if ("`v'"=="scaleversion")    local shortname "sg_scv"
    else if ("`v'"=="typeofgroundtruth") local shortname "sg_gt"
    else if ("`v'"=="samplesize")      local shortname "sg_ss"
    else if ("`v'"=="datatype")        local shortname "sg_dt"
    else if ("`v'"=="modality")        local shortname "sg_mod"
    else if ("`v'"=="wearable")        local shortname "sg_wrb"
    else if ("`v'"=="inoffclinic")     local shortname "sg_ioc"
    else                               local shortname "`v'"

    display "  Short name: `shortname'"

   * Expected run time for demo on a "normal" desktop computer
     
For each csv (on an average sample size 60 studies) the code takes about 2 mins. According to the number (N) of the .csv files in the directory the total run time is 2N.

4.  Instructions for use
   
    * How to run the software on our data
      
  Use the demo .csv file and follow the instructions described in 3. Demo.

    * Reproduction instructions
      
  The output on the sample dataset (motor_pd_coded_allstudies_new.csv) will be a folder "motor_pd_coded_allstudies_new_OUTPUT" that incudes the following produced output used in the paper:

motor_pd_coded_allstudies_new_baujat_results.dta
motor_pd_coded_allstudies_new_BaujatPlotFINAL.gph
motor_pd_coded_allstudies_new_BaujatPlotFINAL.png
motor_pd_coded_allstudies_new_BivBox.gph
motor_pd_coded_allstudies_new_BivBox.png
motor_pd_coded_allstudies_new_Cook4All.gph
motor_pd_coded_allstudies_new_Cook4All.png
motor_pd_coded_allstudies_new_Deeks.gph
motor_pd_coded_allstudies_new_Deeks.png
motor_pd_coded_allstudies_new_ForestPlot.gph
motor_pd_coded_allstudies_new_ForestPlot.png
motor_pd_coded_allstudies_new_ForestPlotResized.gph
motor_pd_coded_allstudies_new_ForestPlotResized.png
motor_pd_coded_allstudies_new_influence_flags.xlsx
motor_pd_coded_allstudies_new_loso_combined.gph
motor_pd_coded_allstudies_new_loso_combined.png
motor_pd_coded_allstudies_new_loso_flags_only.dta
motor_pd_coded_allstudies_new_loso_heterogeneity.gph
motor_pd_coded_allstudies_new_loso_heterogeneity.png
motor_pd_coded_allstudies_new_loso_Q.gph
motor_pd_coded_allstudies_new_loso_Q.png
motor_pd_coded_allstudies_new_loso_results.dta
motor_pd_coded_allstudies_new_loso_snsp.gph
motor_pd_coded_allstudies_new_loso_snsp.png
motor_pd_coded_allstudies_new_META_LOSO.gph
motor_pd_coded_allstudies_new_META_LOSO.png
motor_pd_coded_allstudies_new_Results.txt
motor_pd_coded_allstudies_new_sensitivity_summary.csv
motor_pd_coded_allstudies_new_sensitivity_summary_clean.xlsx
motor_pd_coded_allstudies_new_SROC.gph
motor_pd_coded_allstudies_new_SROC.png


**********************************************
For any question contact:
Prof. Leontios Hadjileontiadis, leontios@auth.gr


