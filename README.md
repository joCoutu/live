#### Install

```sh
# FROM debianLive
sudo passwd user

sudo apt install git ansible ssh sshpass -y
mkdir ~/.ssh/
ssh user@localhost # add to ~/.ssh/known_hosts

git clone https://github.com/jocoutu/live live
cd live
echo "PWD=$(pwd)"
echo 'b(){
    cd $PWD
    if [ -z "$3" ] ; then ALIAS="less $2/README.md"
    else ALIAS=" ansible -i $1 all -m include_role -a name=$2 -e cmd=$3 ${*:4}"; fi
    $ALIAS
}' >> ~/.bashrc
source ~/.bashrc

b 'localhost,' ssh sftp -e user=u1 -e password=p1
sshfs u1@192.168.3.100:/u1 Pictures
```