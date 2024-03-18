# explodingimplosion.github.io
Repository for my github.io page included in my resume with relevant programming examples


Relevant proficiencies with Git:

Scripting and automating Git commits:
  Shortly after moving out to attend university, my brother requested for me to set up his PC to run a Minecraft server. I already had experience with hosting a Minecraft server, but never one that would run independently of my input. I also wanted to make sure that changes to the server world file wouldn't get corrupted. And, if I wanted to switch machines for the server to run on, I wanted the change to be as seamless as possible. GitHub seemed the natural choice. But up until this point, the most experience I had with automating Git was GitHub actions, which still required user input.

  So, after a bit of googling, I arrived on the solution:

  1 - Create a GitHub repo
  2 - Drag the server.jar into the folder (redistributing the .jar isn't legal, so in a public repo it would be prudent to put the jar into the .gitignore)
  3 - Write the following .bat script:

@echo OFF

:loop

java -Xmx4096M -Xms4096M -jar server.jar

echo Press CTRL+C to cancel GitHub commit.

timeout 3

echo (%time%) committing changes to GitHub repo...

For /f "tokens=2-4 delims=/ " %%a in ('date /t') do (set datenow=%%c-%%a-%%b)
git add --all
git commit -m %%datenow%%
echo (%time%) pushing changes to GitHub repo...
git push
echo (%time%) changes pushed(? idk)

echo Press CTRL+C to cancel server restart.

timeout 3

echo (%time%) Restarting server...

goto loop

  I've copy-pasted this code off StackOverflow (because of course) and modified it to suit my needs, and it doesn't work perfectly. The commit titling doesn't work properly, and results in every automatic commit being titled %datenow%. Outside of this, everything works great. The server automatically saves itself whenever it closes, so ______.


  On my to-do list is to automate the server's restarts, so that I don't have to remember to restart the server once or twice a day.


I've applied this same solution to create a multi-PC solution for my college's Smash Ultimate streams. The conundrum we're facing is our powerful stream PC and 'stage setup' is located in an isolated room, away from the majority of competitors. Meanwhile, the ___________. We're also shortstaffed to 3 people, and that number often goes down to 2, since I have other obligations that conflict with the tournament.

The obvious solution is to use TournamentStreamHelper at https://github.com/joaorb64/TournamentStreamHelper, but I'd briefly used this software before, and been burned by it, not properly updating its sets and player info. In scavenging for other resources, I came across Ultimate Stream Tool, which works incredibly well for manual, single-PC updates. Of course, the single-PC part is a problem.
