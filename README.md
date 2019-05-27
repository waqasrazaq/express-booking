# Problem description
Create your own small Express Booking with the JavaScript frontend framework of your choice (e.g. Vue.js, React, or Angular), using the data provided by our Mock API server. 
Please feel free to be as creative as you want. Just make sure that your finished product contains these features:


* A page where the costumer can set a travel date, choose a language, and currency.
* A results section to present the information received from the /booking_availability overview page should, at the very minimum, present the customer with: 

- hotel details ( hotel_details )
  the hotel name
  the address and phone number
- customer support information ( customer_support )
  phone_numbers
  emails
  terms and conditions ( terms_and_conditions )
- room name description rate price value adds

## Technologies used
* VueJS 2
* Vuetify
* Docker
* NGINX


# Installation 

## Prerequisites

Make sure that **Docker** and **Git** is already installed on the system. If not then follow the instructions to download and install these dependencies from the below links
* [Docker](https://www.docker.com/)
* [Git](https://git-scm.com/downloads)

## Steps required to install/run the application
The installation process is quite simple and straightforward. Just follow the below steps

- Open the terminal and navigate into the desired project directory and then execute the below command to download the code from github
```
git clone https://github.com/waqasrazaq/express-booking.git
```

- Once the code is downloaded then navigate into project directory (express-booking)

-  execute the below command to create the docker image of our app
```
$ root@server:~/express-booking# docker build -t express-booking .
```
This will take some time (depending on your internet speed). 

- Once the docker image is created then execute the below command to start the container
```
$ root@server:~/express-booking# docker run -it -p 8080:80 --rm --name express-booking-app-1 express-booking

```

Great, That's it. Installation process is completed. If there's no error till now then we're ready to access the application by simply typing the **localhost:8080** in the broswer.
 

# Working Demo 
Full functioning project is deployed at below url

[http://projectxdubai.com/express-booking/](http://projectxdubai.com/express-booking/)
