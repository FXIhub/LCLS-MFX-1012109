# LCLS-MFX-1012109
two colour convergent beam crystallography experiment with 16M Jungfrau detector

- Experiment Directory: `/sdf/data/lcls/ds/mfx/mfx101210926`

### SSH access
```
# optional
ssh-keygen 
ssh-copy-id amorgan@s3dflogin.slac.stanford.edu

ssh -Y amorgan@s3dflogin.slac.stanford.edu

# optional
ssh-keygen 
ssh-copy-id psana

ssh psana
cd /sdf/data/lcls/ds/mfx/mfx101210926
```

To transfer files over ssh:
```
rsync -vrtlpzh --progress -e 'ssh -A -J amorgan@s3dflogin.slac.stanford.edu:22' amorgan@psana:/sdf/data/lcls/ds/mfx/mfx101210926/results/h5out/r0105_powder.h5 .
```

## Test Jungfrau 16M data
- [Link to lcls docs](https://confluence.slac.stanford.edu/spaces/LCLSIIData/pages/267391733/psana?macroName=view-file&desktop=true#:~:text=psana2%20is%20also%20available%20in%20the%20S3DF,selecting%20%60%60LCLS%20LCLS2%27%27%20for%20the%20Jupyter%20Image.)

```
[amorgan@sdfiana025 analysis]$  source /sdf/group/lcls/ds/ana/sw/conda2/manage/bin/psconda.sh
(ps_20241122) [amorgan@sdfiana025 analysis]$ detnames exp=mfx100852324,run=77,dir=/sdf/data/lcls/ds/prj/public01/xtc
---------------------------
Name            | Data Type
---------------------------
jungfrau        | raw      
epix100_1       | raw      
epix100_0       | raw      
epicsinfo       | epicsinfo
feespec         | raw      
pcav            | raw      
ebeamh          | raw      
MfxDg2BmMon     | raw      
MfxDg1BmMon     | raw      
MfxUsbEncoder01 | raw      
gasdet          | raw      
triginfo        | triginfo 
timing          | raw      
---------------------------

(ps_20241122) [amorgan@sdfiana025 analysis]$ ipython
import psana
ds = psana.DataSource(exp='mfx100852324', run=77, dir='/sdf/data/lcls/ds/prj/public01/xtc')
run = next(ds.runs())
det = run.Detector('jungfrau')
evt = next(run.events())
```

