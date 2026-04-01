# AI-PROGNOSIS-Nature-Aging-Code

AI-driven motor and cognitive decline digital assessment for Parkinson’s disease: a systematic review and meta-analysis

Sofia B. Dias1, Ghada Alhussein2,3, Beatriz Alves2, Margherita Fabbri4, Olivier Rascol4, Maria-Luisa Almarcha-Menargues5, Mónica Kurtis Urra5, Nikos Grammalidis6, Kosmas Dimitropoulos6, Stelios Hadjidimitriou7, Leontios J. Hadjileontiadis7,3, on behalf of the AI-PROGNOSIS Consortium†

submitted to Nature Aging
(please cite it accordingly)
************************************************
To run the whole analysis, use the following .do files that run as batches:

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

The batch files run for every .csv that has the contingency tables and exist in the datafolder. Output folders are automatically created, with all related material (.gph, .png, .xlsx).

Note that in the AI_PROGNOSIS_SubGrouping_FINAL, the covariates explored in the paper were used as names. To avoid any error, update with the names of your covariates, accordingly. Here is the current setting of the covariates' name and short name, that should be edited according to your covariates' names and short names.

* Short names (your mapping)
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

For any question contact:
Prof. Leontios Hadjileontiadis, leontios@auth.gr


