Hello, This is Apurv Sonawane from VJTI, Mumbai. This is the first time I’ll be applying for GSoC. After going through a vast array of Organisations and learning about their projects, I finally found the "*GSoC LMS Portal for Drupal*" project of **Drupal** quite interesting.

## Getting Started

I joined Slack and began digging deeper into the projects. I completed the setup locally and began with the code challenge task mentioned under my project as well. I'm creating this blog to summarise my path of developing a LMS prototype as a pre-proposal task, as well as the hurdles I encountered and how I overcame them.


### 1. Running Drupal locally
- First I followed the [Local Setup using XAMPP](https://www.drupal.org/docs/develop/local-server-setup/windows-development-environment/quick-install-drupal-with-xampp-on) which involved installing it using xampp. I performed all the steps but I got an error about the PHP version.
-  I tried all the steps mentioned on Stack Overflow to get rid of this error but I could not find any solution.
- After some days, I found another setup option using ddev. I did the docker installation by following [this](https://ddev.readthedocs.io/en/latest/users/install/docker-installation/#docker-desktop-for-windows).
- Then, I installed ddev using this particular [Link](https://ddev.readthedocs.io/en/latest/users/install/ddev-installation/).
-  After all the installation, I had to run the following commands:
```
mkdir my-drupal10-site
cd my-drupal10-site
ddev config --project-type=drupal10 --docroot=web --create-docroot
ddev start
ddev composer create drupal/recommended-project
ddev composer require drush/drush
ddev drush site:install --account-name=admin --account-pass=admin -y
ddev drush uli
ddev launch
```
- I also followed this [Link](https://www.drupal.org/docs/installing-drupal/building-a-drupal-site-with-git/) to get the code from git and running it locally.

### 2. A simple webapp demonstrating mini-LMS
- I started by deciding the tech stack to be used, and listing out basic functionalities that an LMS must have.
- As I am quite proficient at the full stack technologies like MERN-Stack, I decided to built my project using MERN. 
-  I began by creating a basic react app using the command.
  ```
  npx create-react-app client
  ```
- I decided to develop the basic landing page for the starters.
- Later I focused on working on the Authentication part.
- For authentication, I used the JWT token. Brcypt.Js was used for hashing the password.
- When it comes to developing different components, initially I began by creating the basic components first. First of all, I developed the navbar and the sidebar using React.
- I began working on the other components, starting with the calender for which, I used FullCalender React Component. I installed dependencies by
  ```
  npm i @fullcalendar/react
  ```
- I used Moment for date and time to display in human readable format.
- After successfully implementing the calender functionality, I went on for the Tasks page where all the tasks would be listed as well as user can add new tasks. For this functionality, I used Axios to make HTTP requests, browseHistory and Redirect from react-router-dom. The same was used to implement the Goals functionality.
- Later I developed the conferencing functionality. Here Socket.Io was used so that client can send and receive messages in real-time with the server. UUIDs are used to uniquely identify entities. @chatscope/chat-ui-kit-react, a library of React components is used to build chat user interfaces quickly and easily.
- Moving on with the flowchart functionality, flowchart.js is used for creating and rendering flowcharts. For the editor, I've used AceEditor which I imported from the react-ace. AceEditor component is used to create an instance of the Ace code editor within a React application. The same was used for the Editor functionality as well.
- Later on moving on with the code collaborators functionality, I've used  judge0 api. Its a free and open source online code editor that allows you to write and execute code
- Simple peer was used to transfer files over rtc and to connect multiple people over a video call.
- [GitHub](https://github.com/Apurv428/Online-Collaboration-Portal)
- [Demo](https://drive.google.com/file/d/1bhSa1p0BOVvyICLqNp6ZbQSuL7dImoa-/view?usp=sharing)
