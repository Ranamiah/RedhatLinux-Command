| Command                     | কেন ব্যবহার করি          |
| --------------------------- | ------------------------ |
| `grep`                      | Search                   |
| `find`                      | File খুঁজতে              |
| `sshd -t`                   | SSH Config Test          |
| `journalctl`                | Error Log                |
| `systemctl status`          | Service Status           |
| `systemctl restart`         | Service Restart          |
| `cat`                       | পুরো File দেখা           |
| `less`                      | বড় File পড়া              |
| `head`                      | প্রথম 10 Line            |
| `tail`                      | শেষ 10 Line              |
| `tail -f`                   | Real-time Log দেখা       |
| `nl -ba`                    | Line Number সহ File দেখা |
| `sed -n`                    | নির্দিষ্ট Line দেখা      |
| `vi`                        | Edit                     |
| `chmod`                     | Permission               |
| `chown`                     | Ownership                |
| `umask`                     | Default Permission       |
| `tar`                       | Backup                   |
| `podman`                    | Container                |
| `nmcli`                     | Network                  |
| `hostnamectl`               | Hostname                 |
| `timedatectl`               | Time/NTP                 |
| `firewall-cmd`              | Firewall                 |
| `getenforce` / `setenforce` | SELinux                  |

RHCSA Linux Command Master Table

| Command             | 📖 কমান্ডের পূর্ণ অর্থ          | 🎯 কেন ব্যবহার করি              | 🧠 গুরুত্বপূর্ণ Option-এর অর্থ                                                          | 💡 কখন ব্যবহার হবে       | ✅ Example                                     | ❌ Common Mistakes             | 📝 মনে রাখার ট্রিক                          |
| ------------------- | ------------------------------- | ------------------------------- | --------------------------------------------------------------------------------------- | ------------------------ | --------------------------------------------- | ----------------------------- | ------------------------------------------- |
| `grep`              | Global Regular Expression Print | File থেকে নির্দিষ্ট Text খুঁজতে | `-i` Ignore Case, `-r` Recursive, `-n` Line Number, `-v` Reverse Match, `-w` Whole Word | Log Search, Error Search | `grep -i error /var/log/messages`             | File Name দিতে ভুলে যাওয়া     | **GREP = Grab Required Expression Pattern** |
| `find`              | Find Files and Directories      | File/Folder খুঁজতে              | `-name`, `-type`, `-size`, `-mtime`, `-user`, `-perm`                                   | File হারিয়ে গেলে         | `find /home -name "*.txt"`                    | Quotes না দেওয়া (`*.txt`)     | **Find = হারানো জিনিস খুঁজে বের করা**       |
| `sshd -t`           | SSH Daemon Test                 | SSH Config ঠিক আছে কিনা পরীক্ষা | `-t` Test Configuration                                                                 | SSH Restart-এর আগে       | `sshd -t`                                     | Test না করেই Restart          | **Restart-এর আগে Test**                     |
| `journalctl`        | Systemd Journal Viewer          | সব System Log দেখা              | `-xe`, `-u`, `-f`, `--since`, `-b`                                                      | Troubleshooting          | `journalctl -xe`                              | Root Permission ছাড়া দেখা     | **Journal = ডায়েরি (Log Book)**             |
| `systemctl status`  | System Control Status           | Service চলছে কিনা               | `status` Service Information                                                            | Service Check            | `systemctl status sshd`                       | Service Name ভুল লেখা         | **Status = বর্তমান অবস্থা**                 |
| `systemctl restart` | Restart Service                 | Service পুনরায় চালানো           | `restart` Restart Service                                                               | Config পরিবর্তনের পরে    | `systemctl restart httpd`                     | Config Test না করা            | **Restart = নতুনভাবে চালু**                 |
| `cat`               | Concatenate                     | পুরো File দেখা                  | `-n` Line Number                                                                        | ছোট File                 | `cat file.txt`                                | বড় File-এ ব্যবহার             | **Cat সব একবারে দেখায়**                     |
| `less`              | Less Pager                      | বড় File পড়া                     | `/` Search, `q` Quit                                                                    | Log File                 | `less messages`                               | `q` না জানা                   | **Less = ধীরে ধীরে পড়া**                    |
| `head`              | Head                            | প্রথম 10 Line                   | `-n` Number of Lines                                                                    | File শুরু দেখা           | `head -20 file.txt`                           | `-n` ভুলে যাওয়া               | **Head = মাথা = শুরু**                      |
| `tail`              | Tail                            | শেষ 10 Line                     | `-n`                                                                                    | File শেষ দেখা            | `tail -20 file.txt`                           | Head/Tail গুলিয়ে ফেলা         | **Tail = লেজ = শেষ**                        |
| `tail -f`           | Follow Tail                     | Real-time Log দেখা              | `-f` Follow                                                                             | Live Monitoring          | `tail -f /var/log/messages`                   | Ctrl+C না জানা                | **Follow = Live**                           |
| `nl -ba`            | Number Lines                    | Line Number সহ দেখা             | `-ba` Number All Lines                                                                  | Config Edit              | `nl -ba file.conf`                            | `cat` দিয়ে Line Count আশা করা | **NL = Number Line**                        |
| `sed -n`            | Stream Editor                   | নির্দিষ্ট Line দেখা             | `-n`, `p` Print                                                                         | Config Check             | `sed -n '20,40p' file`                        | Quotes ভুল                    | **SED = Select Edit Display**               |
| `vi`                | Visual Editor                   | File Edit                       | `i`, `Esc`, `:wq`, `:q!`                                                                | Config Edit              | `vi sshd_config`                              | Insert Mode ভুলে যাওয়া        | **VI = Visual Interface**                   |
| `chmod`             | Change Mode                     | Permission পরিবর্তন             | `+x`, `755`, `644`, `-R`                                                                | Script Execute           | `chmod 755 script.sh`                         | 777 দেওয়া                     | **Mode Change**                             |
| `chown`             | Change Owner                    | Owner পরিবর্তন                  | `user:group`, `-R`                                                                      | Ownership Fix            | `chown apache:apache file`                    | chmod/chown গুলিয়ে ফেলা       | **Own = Owner**                             |
| `umask`             | User Mask                       | Default Permission              | `022`, `027`, `077`                                                                     | New File Permission      | `umask 027`                                   | 777 আশা করা                   | **Mask Permission**                         |
| `tar`               | Tape Archive                    | Backup                          | `-c`, `-x`, `-v`, `-f`, `-z`                                                            | Backup/Restore           | `tar -czvf backup.tar.gz /home`               | Option Order ভুল              | **Create → Zip → Verbose → File**           |
| `podman`            | Pod Manager                     | Container চালানো                | `run`, `ps`, `images`, `stop`, `exec`                                                   | Container Manage         | `podman run nginx`                            | Docker Command Copy করা       | **Podman = Docker Alternative**             |
| `nmcli`             | Network Manager CLI             | Network Configure               | `con show`, `con up`, `dev status`                                                      | IP Change                | `nmcli con show`                              | Interface Name ভুল            | **Network Manager CLI**                     |
| `hostnamectl`       | Hostname Control                | Hostname Change                 | `set-hostname`, `status`                                                                | Server Rename            | `hostnamectl set-hostname server01`           | Reboot দরকার মনে করা          | **Host Name Control**                       |
| `timedatectl`       | Time & Date Control             | Time/NTP                        | `status`, `set-timezone`, `set-ntp true`                                                | Time Fix                 | `timedatectl status`                          | Timezone ভুল                  | **Time Date Control**                       |
| `firewall-cmd`      | Firewall Command                | Firewall Manage                 | `--add-service`, `--reload`, `--list-all`, `--permanent`                                | Port Open                | `firewall-cmd --add-service=http --permanent` | Reload না করা                 | **Permanent → Reload**                      |
| `getenforce`        | Get SELinux Enforcement         | SELinux Status                  | নেই                                                                                     | SELinux Check            | `getenforce`                                  | Status বুঝতে না পারা          | **Get = জানতে চাই**                         |
| `setenforce`        | Set SELinux Enforcement         | SELinux Mode Change             | `0`, `1`                                                                                | Troubleshooting          | `setenforce 0`                                | Permanent মনে করা             | **Set = পরিবর্তন**                          |
| `restorecon`        | Restore SELinux Context         | Context ঠিক করা                 | `-R`, `-v`                                                                              | Web/File সমস্যা          | `restorecon -Rv /var/www/html`                | `chmod` দিয়ে Fix করা          | **Restore Context**                         |
| `crontab`           | Cron Table                      | Scheduled Job                   | `-e`, `-l`, `-r`                                                                        | Automation               | `crontab -e`                                  | Cron Syntax ভুল               | **Cron = Clock Robot**                      |
| `useradd`           | User Add                        | User তৈরি                       | `-m`, `-s`, `-G`, `-u`                                                                  | নতুন User                | `useradd -m rana`                             | Password Set না করা           | **User Add**                                |
| `passwd`            | Password                        | Password Set                    | `-l`, `-u`, `-d`                                                                        | User Password            | `passwd rana`                                 | Root ছাড়া Password Change     | **Pass + Word**                             |
