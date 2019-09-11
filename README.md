## Getting started with Kafka
To get started using Kafka on your local machine, make sure you have an installation of Java 8. Kafka currently only supports Java 8 and nothing higher.

#### Install Java 8 using Homebrew
```sh
brew tap caskroom/versions
brew cask install java8
```
Running `java -version` should confirm the installation.

#### Install Kafka
- Visit the [Apache Kafka download page](https://kafka.apache.org/downloads) and download the `Scala 2.12` binary

- Move the file to a location you can easily navigate to
```sh
  mv ~/Downloads/kafka_2.12-2.3.0.tgz ~
```

- Unpack the files
```sh
cd ~ && tar -xvf kafka_2.12-2.3.0.tgz
```

If everything went correctly, you should now be able run any of the kafka commands; like so
```sh
cd kafka_2.12-2.3.0
bin/kafka-topics.sh
```

If you see the help for the command you just ran, everything is working and your machine is correctly configured to run Kafka.

#### Convenience
Since all kafka commands are located in a nested `bin` directory, we will need to `cd` into that directory every time we want to run kafka commands. To make our lives easier, let's add the Kafka `bin` directory to our `PATH`
**Once you save the file, reload the terminal session (or start a new one)**
```sh
# ~/.zshrc if you're using zsh
sudo vi ~/.bash_profile
  
# At the very end of that file
export PATH="$PATH:path/to/kafka/bin"
```

#### Starting Kafka
To work with Kafak, we need to have Zookeeper and Kafka servers running.

Start Zookeeper & Kafka
```sh
zookeeper-server-start.sh /path/to/kafka/config/zookeeper.properties
kafka-server-start.sh /path/to/kafka/config/server.properties
```