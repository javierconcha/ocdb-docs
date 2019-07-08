# Field name modifiers and suffixes

## Modifiers
The table below lists acceptable modifiers to modify field names. They must be appended after the base name (and wavelength, if any) but before any suffix.

| Field Modifiers |  Units |  Description  | 
|------------|--------|---------------|

| _###ang | does not change base field's units | Collection angle. Append '_###ang' to the end of a field name to indicate the collection angle a measurment (such as VSF) was taken at |  where '###' would be replaced by the float or integer representation of an angle in degrees. (For example |  if volume scattering function is measured at a collection angle of 124 degrees |  the field name would be 'vsf_124ang'.) |
| _##cilo | does not change base field's units | Confidence interval |  lower |  where ## is to be replaced with the percent the confidence interval was computed for. Append '_##cilo' to the end of the field name it describes to indicate the relative confidence interval at a given percentage |  e.g. |  chl_95cilo |
| _##ciup | does not change base field's units | Confidence interval |  upper |  where ## is to be replaced with the percent the confidence interval was computed for. Append '_##ciup' to the end of the field name it describes to indicate the relative confidence interval at a given percentage |  e.g. |  chl_95ciup |
| _ex### | does not change base field's units | Excitation wavelength. Append '_ex###' to the end of a field name to indicate the wavelength of excitation the measurement was taken at |  where '###' would be replaced by the float or integer represenation of wavelength in nm. May be used in combination with '_em###' |  as such: 'cdmf_ex###_em###' |  where '_ex###' preceeds '_em###'. |
| _em### | does not change base field's units | Emission wavelength. Append '_em###' to the end of a field name to indicate the wavelength of emission the measurement was taken at |  where '###' would be replaced by the float or integer represenation of wavelength in nm. May be used in combination with '_ex###' |  as such: 'cdmf_ex###_em###' |  where '_ex###' preceeds '_em###'. |
| _###filt | does not change base field's units | Append this suffix to report the filter size that observed measurements are larger than |  where ### is the number of micrometers of the filter size (i.e. |  this is for size fractionated measurements that did not pass through the reported filter size.) Unless this suffix is used |  it is assumed the methodology used a standard filter size. If combined with ###prefilt |  order these 2 suffixes sequentially with ###filt first (e.g. |  Chl_5filt_200prefilt). |
| _###prefilt | does not change base field's units | Append this suffix to report the filter size that observed measurements are smaller than |  where ### is the number of micrometers of the filter size (i.e. |  this is for size fractionated measurements that passed through the reported filter size.) Unless this suffix is used |  measurements are assumed to be from unfiltered or whole water. If combined with ###filt |  order these 2 suffixes sequentially with ###filt first (e.g. |  Chl_5filt_200prefilt). |
| _###ppt | does not change base field's units | Parts per thousand. Append '_###ppt' to the end of a field name to indicate the solution's concentration that a measurement was taken in |  where '###' would be replaced by the concentration as a floating point number or integer. (For example |  if absorbance is measured at 435.2 nm in a 35.3 ppt sodium-chloride solution |  the field name would be 'abs_nacl435.2_35.3ppt'.) |
| _###size | does not change base field's units | Median bin diameter in microns. Used as a suffix for the field 'PSD'. |
| _stokes1 | does not change base field's units | First Stokes parameter for characterizing polarization. |
| _stokes2 | does not change base field's units | Second Stokes parameter for characterizing polarization. |
| _stokes3 | does not change base field's units | Third Stokes parameter for characterizing polarization. |
| _stokes4 | does not change base field's units | Fourth Stokes parameter for characterizing polarization. |

## Suffix
The table below lists acceptable suffixes to modify field names. They must be appended at the end of field name, after any modifiers or wavelength. For any field including a suffix, a corresponding field (without suffix) must exist (e.g. if Rrs442.5_sd is provided, Rrs442.5 must exist).

| Field Modifiers |  Units |  Description  | 
|------------|--------|---------------|
| _abun | cell/L | cell abundance for a particular (phytoplankton) taxonomic type | 
| _biovol | m^3/L | bio-volume for a particular (phytoplankton) taxonomic type | 
| _carbon | ug/L | carbon concentration for a particular (phytoplankton) taxonomic type | 
| _bincount | none | Number of records averaged into a bin or reported measurement specific to the prefix that _bincount is attached to. The field bincount can simply be used if the bincount applies to all forms of data in the file but this field suffix (i.e. '<field>_bincount') can be used multiple times in the same file for field-specific numbers. | 
| _cv | unitless | Coefficient of Variation |  
| _sd | same as base field's units | Standard Deviation.  | 
| _se | same as base field's units | Standard Error.  | 
