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

#solution for the idempotence of containers:
#search in the state of the container and if nothing is present the container is created.
- name:
  containers.podman.podman_container_info:
    name: 'mariadb_test'
  register: 'db_info'

- name:
  containers.podman.podman_container:
    name: 'mariadb_test'
      [...]
  when: "not db_info.containers"
