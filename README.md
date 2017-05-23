# Http sweet Http 

This project borns with the article <a href="https://www.codeproject.com/Articles/1188394/Http-sweet-Http-with-gastona">Http sweet Http (with gastona)</a>
it will be the repository to keep the samples updated and add additional ones following the same
idea of being very simple examples showing all the features of the "gastona technology".

Following a copy of the article introduction

## Introduction

It is well known that HTTP is the protocol of the Web, what is probably less known by many people is that the base idea of HTTP is indeed quite simple and can be used for many other applications even not related with internet.

An example of such application and very useful nowadays would be communicating devices that are attached to a home WLAN. For instance a PC with a smart phone, a tablet etc.

In this article we show how to do it and for that we will implement some basic but quite demonstrative functionalities like getting a screenshot from the PC, interchanging files (download and upload) and save notes into the PC written from a device.

The demos use a convenient and tiny HTTP server but they differ from typical Web applications in several ways. Thought to be ran in a secured network like a home WLAN there is no need to deal with security issues. Also because of this we can make the server play any role we want thus having full control of it which can not the case in a usual web application.