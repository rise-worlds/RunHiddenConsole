# RunHiddenConsole
Hide console window for windows programs

What it does.
-------------
RunHiddenConsole is a lite program for hiding console window,it running on windows,like a linux command line end with '&',
Let the program run behind without bloking console.

Usages.
-------------

    RunHiddenConsole.exe [/v] [/e] [/l] [/w] [/o output-file] commandline

    Options:
      /v                Print the program version
      /e                Copy host process environment to child process at startup
      /l                Print the result of process startup
      /w                Wait for termination of the process
      /o output-file    Redirect the output of the program to a file

    Examples:
      RunHiddenConsole.exe /l e:\\WNMP\\PHP\\php-cgi.exe -b 127.0.0.1:9000 -c e:\\WNMP\\php\\php.ini
      RunHiddenConsole.exe /l E:/WNMP/nginx/nginx.exe -p E:/WNMP/nginx
