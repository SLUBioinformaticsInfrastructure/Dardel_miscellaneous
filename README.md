# Dardel_miscellaneous
This is a repository for all the small things that make life easier and should be kept in mind when running projects on Dardel. 


## Scratch

Your home directory on Dardel is capped at 25 GB. 

PDS's scratch however, has no cap and can be used for temporary large files. All data gets automatically removed after 30 days. 

```{.bash}
cd $PDC_TMP
```

### Conda, singularity and apptainer and scratch

To prevent conda, singularity or apptainer to use up precious storage in your home directory, you can set their package directories/ cache directories to scratch. 

In you home directory, open the hidden file `.bashrc`. Add, save and re-start the ssh connection: 

```{.bash}
# Set conda package location
export CONDA_PKGS_DIRS=$PDC_TMP/conda/packages

# Set Apptainer build path for temporarily pulling and converting images
export SINGULARITY_CACHE=$PDC_TMP/singularity/cache
export APPTAINER_CACHE=$PDC_TMP/apptainer/cache
```

## clean out apptainer cache every now and then to prevent clogging your home directory

```{.bash}
apptainer cache clean 
```

## backups on Dardel

Remember: nothing is backed up on Dardel

## Home directory

Your home directory is visible to everyone, unless you change permissions. 
It has a hard ceiling on the number of files - see above on how set up your apptainer or conda if you use it to not run into this ceiling. 

## Permission in shared projects

In a shared project on Dardel, group members do not automatically have write permissions. 

## access to files

Check down below for `Access Control Lists`, to give specific users permission to files you own. This is necessary when working in a shared project.

https://support.pdc.kth.se/doc/support/?section=/doc/support-docs/basics/quickstart

## project information

`groups`will give you a list of the projects you have access to. 

`projinfo` will give you more information on the projects your are a part of - resources limits and usage etc. 

## which partition should I run my analyses from?

https://nf-co.re/configs/pdc_kth/

## download NGI data to Dardel

Data download on Dardel: For data downloads on Dardel, please log into the dedicated file transfer node: [dardel-ftn01.pdc.kth.se](http://dardel-ftn01.pdc.kth.se/). Do NOT submit data-transfer jobs to the queueing system, run them directly on that node.

## GitHub ssh setup on Dardel

When adding a key to be able to clone a private repos on dardel, make sure that the private key name is a default one, _e.g._ `id_rsa` and not `id_rsa.pdc`. Or add a GitHub block in your ~/.ssh/config on dardel that contains the `IdentityFile`.

Example of config:

```
Host github.com
	IdentityFile ~/.ssh/id_rsa.github
	User git
```

## central databases

are located here: 

```
/pdc/software/resources/blastdb/
```

and can be reached with the following shortcut: `$BLASTDB`. 
