# Program AB

Program AB is the reference implementation of the AIML 2.0 draft specification.
AIML is a widely adopted standard for creating chat bots and mobile virtual assistants like ALICE, Mitsuku, English Tutor, The Professor, S.U.P.E.R. and many more.
Forked from: [https://code.google.com/p/program-ab/](https://code.google.com/p/program-ab/)

## Installation

Add to your pom.xml:
```xml
    <repositories>
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
	</repositories>

	<dependencies>
        <dependency>
            <groupId>com.github.haggaishachar</groupId>
            <artifactId>program-ab</artifactId>
            <version>v1.0</version>
        </dependency>
	</dependencies>
```

## Install the 'ALICE' and 'Super' AIML files (optional)

```xml
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-dependency-plugin</artifactId>
                <version>2.10</version>
                <executions>
                    <execution>
                        <id>unpack-dependencies</id>
                        <phase>install</phase>
                        <goals>
                            <goal>unpack-dependencies</goal>
                        </goals>
                        <configuration>
                            <includes>bots/**</includes>
                            <outputDirectory>${user.dir}</outputDirectory>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
```

## Usage

```java
        String path = System.getProperty("user.dir"); // or any other directory with the AIML files.
        String name = "alice2";
        String action = "chat";

        Bot bot = new Bot(name, path, action);
        Chat chatSession = new Chat(bot);

        while (true) {
            System.out.print("human: ");
            String textLine = IOUtils.readInputTextLine();

            if (textLine == null || textLine.equals("q")) {
                bot.writeQuit();
                System.exit(0);
            }

            String response = chatSession.multisentenceRespond(textLine);
            System.out.println(name + ": " +  response);

        }
```

## License

GNU Lesser General Public License