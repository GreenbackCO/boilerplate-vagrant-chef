# boilerplate-vagrant-chef
Project boilerplate for running local vagrant projects using chef-solo.

### Project Directory Structure

|-- Client folder
  |-- CHEF ( base-chef repo, common server setup )
    |-- data_bags
    |-- cookbooks
    |-- environment
    |-- recipes
    |-- roles
  |-- PROJECT-ABBR
    |-- chef-repo ( project specific chef setup )
      |-- data_bags
      |-- cookbooks
      |-- environment
      |-- recipes
      |-- roles
    |-- Project files and folders.....
