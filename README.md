# tedious-to-llm
Let the LLM handle the tedious tasks.

When you look back at log files later, you might find yourself wondering, “Wait, what was that task again?” or
“Why did I edit that file at that time?”—in other words, even when you look at raw logs as a sort of scrapbook,
there are times when you just can’t figure it out, right?

This tool is designed to address that very issue.

Here’s what it does:

1. Starts logging (script logs)
2. After a set period of time, annotations are added to the log

That’s it—just those two steps. It’s not a big deal, but it’s handy to have.

Please run it as follows:

```bash
vim .bashrc
export OPENAI_API_KEY=sk-proj-xxxxxxxxxx
export OPENAI_MODEL="gpt-4.1-mini"
:wq

source .bashrc

git clone git@github.com:nw-engineer/tedious-to-llm.git
cp -r tedious-to-llm/bin
cp tedious-to-llm/
chmod +x ~/bin/worklog
cp tedious-to-llm/watch_session.py ~/

~/bin/worklog
```

- Logs are stored in the `scraplogs` directory.
- Press Ctrl + Z when you're done.

#### Execution Results
```bash
=== chunk summary ===
概要: dockerコンテナの稼働状況を確認した
Script started on 2026-03-17 18:11:27+09:00 [TERM="xterm" TTY="/dev/pts/1" COLUMNS="150" LINES="40"]
xxxxxxx@docker001:~$
xxxxxxx@docker001:~$
xxxxxxx@docker001:~$
xxxxxxx@docker001:~$
xxxxxxx@docker001:~$
xxxxxxx@docker001:~$

注釈: dockerで稼働中コンテナ一覧を表示
xxxxxxx@docker001:~$ docker ps

CONTAINER ID   IMAGE                     COMMAND                  CREATED       STATUS                PORTS                                                                                                 NAMES
3ea2896244f2   demo-proxy-nginx          "/docker-entrypoint.…"   13 days ago   Up 13 days            127.0.0.1:32790->80/tcp                                                                               demo-proxy-nginx-1
8a7741746cff   demo-proxy-app            "java -jar /app/app.…"   13 days ago   Up 13 days            8080/tcp                                                                                              demo-proxy-app-1
2367a672bf28   gitlab/gitlab-ce:latest   "/assets/init-contai…"   2 weeks ago   Up 5 days (healthy)   80/tcp, 443/tcp, 0.0.0.0:8081->8081/tcp, :::8081->8081/tcp, 0.0.0.0:2222->22/tcp, [::]:2222->22/tcp   gitlab
b52cd83cb4f1   devops-stack-jenkins      "/usr/bin/tini -- /u…"   2 weeks ago   Up 2 weeks            50000/tcp, 0.0.0.0:8082->8080/tcp, [::]:8082->8080/tcp                                                jenkins
xxxxxxx@docker001:~$

exit

Script done on 2026-03-17 18:11:51+09:00 [COMMAND_EXIT_CODE="0"]
```

If you plan to use it extensively, please switch to a local LLM.

Have a great life!