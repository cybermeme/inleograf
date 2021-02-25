#before any other action, consider the following tasks

#Configure vim for yml
echo "set bg=dark
autocmd FileType yaml setlocal ai et ts=2 sw=3 cuc cul">~/.vimrc

#install collections for our roles
ansible-galaxy collection install community.general
ansible-galaxy collection install containers.podman
ansible-galaxy collection install ansible.posix

#grab the servers ssh fingerprint
ssh-keyscan $serversIPs >> ~/.ssh/known_hosts

