# Setting off a validation run

- Using DbForge drop all tables and sequences from existing schema that you will use (e.g. `star_validation`),
  the drop.sql file on the shared drive can be used for this :
  `\\sharefs6\UCLH6\EMAP\Shared\EmapSqlScripts\devops\drop.sql`
- On the GAE checkout up to date versions of all branches in the repository that uses the correct schema 
  (e.g. star_validation is in `/gae/star-validation`). Use tmux or screen if you don't hate yourself.
- in emap core directory run: 



```
shell script

./emap-live.sh build # build all services

source 

scripts/validation/run_validation.sh # may want to give custom start and end run time 

```


