## Part 1
```
import java.io.IOException;
import java.net.URI;
import java.util.*;

class Handler implements URLHandler {
    String str="";

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                str+=parameters[1]+"\n";
            }
        }
        return str;
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

After running the code, two lines of strings were entered into the url: "line 1 of strings" and "line 2 of strings". This was able to see the code work with chars and ints. In the end, they were all converted to strings.

![sc1](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report2/addmessagess.PNG?raw=true)
![sc2](https://github.com/jliu0140/cse15l-lab-reports/blob/main/report2/addmessagess2.PNG?raw=true)

## Part 2
