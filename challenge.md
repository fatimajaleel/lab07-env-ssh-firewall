# Lab 07 Challenge: Environment Audit and Ping Block

## Job 1: Environment Variables

Commands:
- printenv | grep '^PATH='
- printenv | grep '^LANG='
- printenv | grep '^PWD='
Answers:
- PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/fatimajaleel
- LANG=en_US.UTF-8
- PWD=/home/fatimajaleel/lab07-env-ssh-firewall

## Job 2: Temporary Student Variables

Commands:
- export STUDENT_NAME="Fatima Jaleel"
- export STUDENT_ROLL_NUMBER="FA24B1-SE-037"
- export STUDENT_SEMESTER="5th Semester"
- printenv | grep '^STUDENT_'

Answers:
- STUDENT_NAME=Fatima Jaleel
- STUDENT_ROLL_NUMBER=FA24B1-SE-037
- STUDENT_SEMESTER=5th Semester

Persistence test:
- Logged out and logged in again.
- Command: printenv | grep '^STUDENT_'
- Result: No output because temporary variables disappeared.

## Job 3: Permanent Student Variables

Commands:
- Added the three STUDENT_ variables to ~/.bashrc
- source ~/.bashrc
- Logged out and logged in again.
- printenv | grep '^STUDENT_'

Answers:
- STUDENT_NAME=Fatima Jaleel
- STUDENT_ROLL_NUMBER=FA24B1-SE-037
- STUDENT_SEMESTER=5th Semester
- Result: All three variables appeared after a new login.

## Job 4: Block and Restore Ping

Commands:
- Tested ping from Windows.
- sudo cp /etc/ufw/before.rules ~/before.rules.backup
- Edited incoming echo-request rule from ACCEPT to DROP.
- sudo ufw reload
- Tested ping again from Windows.
- Restored DROP to ACCEPT.
- sudo ufw reload

Results:
- Initial ping: Successful replies received.
- Ping after blocking: 4 packets sent, 0 received, 100% packet loss.
- Ping after restoring: Successful replies received.
- Final firewall rule: ACCEPT
