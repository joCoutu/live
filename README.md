#### Install

```sh
# FROM debianLive
sudo passwd user

sudo apt install git ansible ssh sshpass -y
ssh-keyscan -H localhost >> ~/.ssh/known_hosts

git clone https://github.com/jocoutu/live live
cd live
echo 'b(){
    cd $PWD
    if [ -z "$3" ] ; then ALIAS="less $2/README.md"
    else ALIAS=" ansible -i $1 all -m include_role -a name=$2 -e cmd=$3 ${*:4}"; fi
    $ALIAS
}' >> ~/.bashrc
source ~/.bashrc

b 'localhost,' ssh sftp -e user=user1 -e password=p1
sshfs user1@192.168.3.100:/user1 nas
```