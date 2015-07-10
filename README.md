# Run14AuAu200GeV_StRefMultCorr
LBNL - STAR Experiment, Relativistic Heavy Ion Collider (RHIC), BNL  
RHIC year 2014 Run, with Heavy Flavor Tracker

## Declaration
This code was original inherit form Hiroshi Masui And Dr. Alexander Schmah

###Code Authors:  
[Guannan Xie](https://github.com/GuannanXie) (guannanxie@lbl.gov)  
Hiroshi Masui (HMasui@lbl.gov)   
Alexander Schmah(ASchmah@lbl.gov)   
- - -

###How to use this code:  
```bash
# Load StRefMultCorr library
# NOTE: Add this line in your 'macro', not in the source code
gSystem->Load("StRefMultCorr");
# For grefmult
StRefMultCorr* grefmultCorrUtil = CentralityMaker::instance()->getgRefMultCorr() ;
grefmultCorrUtil->init(15075008);
grefmultCorrUtil->setVzForWeight(6, -6.0, 6.0);
grefmultCorrUtil->readScaleForWeight("StRoot/StRefMultCorr/macros/weight_grefmult_vpd30_vpd5_Run14.txt");
for(Int_t i=0;i<6;i++){
cout << i << " " << grefmultCorrUtil->get(i, 0) << endl;
}

# NOTE: Add this line inside the source code
grefmultCorrUtil->initEvent(grefmult, vz, zdcCoincidenceRate) ;
# see StRefMultCorr.h for the definition of centrality bins
# Centrality from grefmult
const Int_t cent16_grefmult = grefmultCorrUtil->getCentralityBin16() ;
const Int_t cent9_grefmult  = grefmultCorrUtil->getCentralityBin9() ;
# Re-weighting corrections for peripheral bins
const Double_t reweight_grefmult = grefmultCorrUtil->getWeight() ;
# Corrected refmult (with z-vertex dependent correction and luminositiy correction)
# NOTE: type should be double or float, not integer
const Double_t grefmultCor = grefmultCorrUtil->getRefMultCorr() ;
```
