Create an alias to avoid mucking about with hosts files:

    alias ansible='ansible -i hosts'

Check connections

    ansible all -m ping
