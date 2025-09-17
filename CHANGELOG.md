# Changelog

All notable changes to this project are documented in this file. See
[Conventional Commits](https://conventionalcommits.org) for commit guidelines.

# [1.1.0](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/compare/1.0.0...1.1.0) (2025-09-17)


### Features

* Support latest Ubuntu 22.04 image ([#2](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/issues/2)) ([a33226f](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/a33226f166e47687244b55c695204cf6663bde34))

# 1.0.0 (2025-09-04)


### Bug Fixes

* Remove unnecessary user input for IPA server IP ([b277e59](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/b277e5940b9187c72316c7f0fe706446fc6141b4))


### Features

* Add retry during IPA client enrollment to mitigate transient errors ([80af5f5](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/80af5f53d328aa90b629fb7c0430a541f3b80a41))
* Clean old enrollment data form IPA server if new host claims pre-existing FQDN ([8122856](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/81228568f0feeaa3fa3860f2dd9225e2eff4cdda))
* Configure and enable System Security Service Demon on RockyLinux hosts ([466d164](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/466d1640b7d8cfcf15401b289496e1db0f855659))
* Configure IPA client based on user input ([1916bc9](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/1916bc955360b2b5b202c6b7eb70d8c7aab2d2d5))
* Downgrade supported distributions to Rocky 8 and Ubuntu 22 ([28434e1](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/28434e1cef176a8cc4c2b6d8e0104d14c51e4651))
* Enable access via public key or password from user-define IPs ([bbec8fc](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/bbec8fc0896a20c803815045736110d714c277c8))
* Install and list versions of core requirements ([0a4f7b2](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/0a4f7b236b58edd1cd885e539da216bf3e9c71db))
* Linux distro check to ensure deployment on RockyLinux 8/9 and Ubuntu 22/24 only ([165451d](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/165451dd1b2c5b24a4453e347236fb040e3bd83a))
* Overwrite domain name and host name according to user input ([6d4a759](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/6d4a759b7b250abbe009b5b10576561d6087b9e3))
* Pin packages versions ([8075d19](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/8075d19bc1207340f389407607a0c3aa188a409b))
* Prevent credential leaks into logs upon task failure ([81f22df](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/81f22dfac89516acacd84c6c56da1c5a8bfa87c8))
* Restrict supported Linux distros down to the minor version ([0b77077](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/0b770775bcd6c4423b5a1c41ee8d839df0403f95))
* Set fallback value for whitelisted IP ranges if no user-defined ([3979619](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/39796199ff9ef24d963500ed5b476481523fd7d1))
* Validate inputs to prevent SSHD or IPA breakdown and remove input defaults ([441942e](https://github.com/ewcloud/ewc-ansible-role-ipa-client-enroll/commit/441942eec425037669749606820115213577f901))
