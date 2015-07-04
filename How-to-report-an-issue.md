You need to report an issue and all of the troubleshooting steps are not working for you. Please follow the steps in order for us to resolve the issue as soon as possible.

1. Stop PopcornTV.
2. Delete ``PopcornTV.log`` from the application folder.
3. Start PopcornTV using ``sudo node atv.js Debug`` (Please make sure to leave off ``sudo`` if you are on a windows machine)
4. Repeat the exact issue.
5. Stop PopcornTV.
6. Upload the contents of ``PopcornTV.log`` to a [Github Gist](http://gist.github.com) or onto [Pastebin](http://pastebin.com)
7. Upload the contents of ``aTVSettings.json`` to a [Github Gist](http://gist.github.com) or onto [Pastebin](http://pastebin.com)
8. [Report](https://github.com/OstlerDev/PopcornTV/issues/new) how to repeat the error in the issue as well as the outcome that you expected to get. Please be sure to include a link to the log and settings file that you uploaded to [Gist](http://gist.github.com) or onto [Pastebin](http://pastebin.com).

Note: When running in Debug mode all logs are sent up to the logging server. The logs are kept for 7 days then deleted permanently.