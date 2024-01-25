#### Install

```sh
# FROM debianLive
sudo passwd user

sudo apt install git ansible -y
git clone https://github.com/jocoutu/live live
echo "b(){
    cd $PWD
    if [ -z "$3" ] ; then ALIAS="less live/roles/$2/README.md"
    else ALIAS=" ansible -i $1 all -m include_role -a name=live/roles/$2 -e cmd=$3 ${*:4}"; fi
    $ALIAS
}" >> ~/.bashrc
source ~/.bashrc
```