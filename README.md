# Ass1
first assignment
https://github.com/alonmutzary/Ass1.git
## 📁 Project Structure

```
Project/
│   .gitignore
│   CMakeLists.txt
│   docker-compose.yml
│   Dockerfile.client
│   Dockerfile.server
│   Dockerfile.tests
│   README.md
│
├───src
│   ├───client
│   │       main.py
│   │       tcp_client.py
│   │       user_interface.py
│   │
│   └───server
│           BitArrayLoader.cpp /.h
│           BitArraySaver.cpp /.h
│           BloomFilter.cpp /.h
│           IHashFunction.h
│           ILoader.h
│           ISaver.h
│           LogicHandler.cpp /.h
│           main.cpp
│           Server.cpp /.h
│           SocketManager.cpp /.h
│           StdHash.h
│           UrlFileLoader.cpp /.h
│           UrlFileSaver.cpp /.h
│
└───tests
        test_BitArraySaver.cpp
        test_bloom.cpp
        test_FileLoader.cpp
        test_LogicHandler.cpp
        test_Server.cpp
        test_SocketManager.cpp
        test_UrlFileSaver.cpp
```

## Questions
### Did the fact that the command names changed require you to modify code that is supposed to be "closed for modification but open for extension"?  
Yes. 
In the last version we handled the commands in the main.cpp and therefor the code was not closed for modifications. This is not caused specifically by the command names but by the fact that we could not handle it in the main anymore.  
In this version, the commands are being handled by the Logic Handler and therefore if we will need to change the command names again we will just change one or two lines to adapt the code to the changes.  
  
### Did the fact that new commands were added require you to modify code that is supposed to be "closed for modification but open for extension"?  
No.  
Since we created the Logic Handler we only needed to add the new command to LogicHandler.cpp.  
The idea of single responsibility per class and making the Logic Handler open for extension made it easy to add.  
  
### Did the fact that the command output format changed require you to modify code that is supposed to be "closed for modification but open for extension"?  
No.  
Just like adding commands, the after creating Logic Handler it was easy to change the output since we only rewrote the strings.  
The idea of single responsibility per class and making the Logic Handler open for extension made it easy to add.  

### Did the fact that input/output now comes from sockets instead of the console require you to modify code that is supposed to be "closed for modification but open for extension"?  
Yes.  
In the last version we used cin and cout for I/O and now we changed it completely to use socket for I/O.  
We made a different structure in the new version that has more abstract handling of I/O for future use of more than one client.
