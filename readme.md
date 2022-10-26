

- name: http
  become: yes
  firewalld:
    port: 80/tcp
    permanent: yes
    state: enabled

- name: https
  become: yes
  firewalld:
    port: 443/tcp
    permanent: yes
    state: enabled


  - name: FirewallD rules
    firewalld:
      permanent: yes
      immediate: yes
      service: "{{ item }}"
      state: enabled
    loop:
      - http
      - https