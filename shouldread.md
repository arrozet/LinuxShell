In user directory ,
    cd 
[WINDOWS->LINUX]to copy the folder where shell is to home/shell do:
    sudo cp -r  /mnt/d/\!UMA/\!\!UMA_CODE/2/2cuatri/SO/shell/ /home/roz/
// esto va pero no borra los archivos que ya estén. solo sobreescribe y añade
[LINUX->WINDOWS,fromshellDirectory]
    sudo cp -r  /home/roz/shell /mnt/d/\!UMA/\!\!UMA_CODE/2/2cuatri/SO/ 
To compile with all flags do:
1. First go to the directory
    cd /shell/Shell_project-ROZ/Shell_project/

2. Compile
    gcc -Wall -Wextra -O2 -D_GLIBCXX_DEBUG Shell_project.c job_control.c -o shell

3. Execute
    ./shell