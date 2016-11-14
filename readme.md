# .NET & Visual Studio

## IDE = _Interactive Development Environment_   

## When create a project for the web application using the Visual studio
  - When name the file use the same case as nameSpace camal case and conventionally name the file after the namespace

## Solution is a collection of the projects. Most apps have more than one project.  
  - Add source control check box put projects in the directory

## Then Choose which visual studio version to use

## Github ... choose gitignor file to Visual studio 

# .NET - create new application

```
create new PROJECT in powershell
md newproject
cd newproject
dotnet new

- we need to restore some packages by telling what's pkges will be use"
- update project.json file by
dotnet restore
  - will install dependencies project.json need
dotnet run
  - compile the file

In Visual studio code (written in the language: TypeScript)
- run code .
  - call code . to open
    If write program
    {
      Console.WriteLine("Hello world");
      var name = Console.ReadLine();
      Console.WriteLine("Hello {0} welcome to c#", name)
      //Tthe {0}  will be replaced by name
      or can also write it this way instead
      Console.WriteLine($"Hello {name} welcome to c#");
    }
- will notice that it's a c# application
- will auto create vscode folder
Ctrl + ` will open up Command prompt(terminal or powershell)

- We will need a web server in order to see code in browser
- Go to project.json to add dependencies  in vscode
  - under dependencies of "Microsoft.NETCore.App"
  - Add after }
  -,
   "Microsoft.AspNetCore.Server.Kestrel": "1.0.1"(pick ther latest version) (Kestrel is a dotNet core web server)
   - in command line that open in the vs code. it'll run automatically dotnet restore when click restore
-After add the pkg, in Application type we need to save it in order to use it
  using: Microsoft.AspNetCore.Builder;
  using: Microsoft.AspNetCore.Hosting;
  using: Microsoft.AspNetCore.Http;
  *****Below would already be build in VS Studio Once type in using!
    public class Startup
    {
      public void Configure(IApplicationBuilder app) //Configure will set everything up
      {
        app.Run(
            Context =>
            {
              return context.Response.WriteAsync (=response.writeLine)
            }
          );//now we build our host we'll need to run our host
      }
    }
    in public static void Main()
    {then we need to set
      var host = new WebHostBuilder().UseKestrel()
      .UserStartup<Startup>()
      .Build(); (host web application Now we need to add class Startup above)

      //now we need to run the host in order to tell the program to run it (if not run it'll just show up in command linet)
    host.run();
    }
  -now the command line will say to look at localhost ...

  -when project is modified (change) then we need to stop and run it again

  -To refresh the page add tool "dotNetWatch" = a dependencies that will be use during the compile time
  add to project.json file by add tools Section
},
"tools": {
  "Microsoft.DotNet.Watcher.Tools": {
    "version": "1.0.0-*",
    "imports": "portable-net451+win*"
  }
}

run dotNet restore
run dotNet watch run

```
## more info go to dot.Net documentation

# Visual Studio Keyboard Shortcuts
| Command | Key
| ------ | :-------:
|Start |	F5
|Start Without Debugging |	Ctrl+F5
|Restart |	Ctrl+Shift+F5
|Run to Cursor |	Ctrl+F10
|Step Into |	F11
|Step Out |	Shift+F11
|Step Over |	F10
|Stop Debugging |	Shift+F5
|Select All |	Ctrl+A
|Select Current Word |	Ctrl+W
|Copy |	Ctrl+C
|Cut |	Ctrl+X
|Copy Entire Line |	Ctrl+C
|Cut Entire Line |	Ctrl+X
|Paste |	Ctrl+V
|Undo |	Ctrl+Z
|Redo |	Ctrl+Y
|Find |	Ctrl+F
|Find All References |	Shift+F12
|Find In Files |	Ctrl+Shift+F
|Find Next |	F3
|Find Previous |	Shift+F3
|Replace |	Ctrl+H
|Replace in Files |	Ctrl+Shift+H
|  Build Solution	| Ctrl+Shift+B
|Go To End of Document |	Ctrl+End
|Go To Beginning of Document |	Ctrl+Home
|Got To Matching Brace |	Ctrl+]
|Go To Next Word |	Ctrl+Right
|Go To Previous Word |	Ctrl+Left
|Go To Line |	Ctrl+G
|Go To Declaration |	Ctrl+F12
|Go To Definition |	F12
|Navigate Backwards |	Ctrl+-
|Navigate Forewards |	Ctrl+Shift+-
|Next Tab |	Ctrl+Alt+Page Down
|Previous Tab |	Ctrl+Alt+Page Up
|Quick Launch |	Ctrl+Q
|Complete Word |	Ctrl+Space
|List Members |	Ctrl+J
|Paremeter Info |	Ctrl+Shift+Space
|Peek at Definition |	Alt+F12
|Quick Info |	Ctrl+K, Ctrl+I
|Close Popup Window |	Esc
|Make Lowercase |	Ctrl+U
|Make Uppercase |	Ctrl+Shift+U
|Move Selected Lines Up |	Alt+Up
|Move Selected Lines Down |	Alt+Down
|Indent |	Tab
|Unindent |	Shift+Tab
|Format Document |	Ctrl+K, Ctrl+D
|Format Selection |	Ctrl+K, Ctrl+F
|Comment Section |	Ctrl+K, Ctrl+C
|Uncomment Section |	Ctrl+K, Ctrl+U
|Rename |	Ctrl+R, Ctrl+R
|Extract Method |	Ctrl+R, Ctrl+M
|Remove Parameters |	Ctrl+R, Ctrl+V
|Reorder Parameters |	Ctrl+R, Ctrl+O
| Compile	| Ctrl+F7
|Hold down shift to hightlight everything between the cursor and where the cursor ends up
|Zoom In / Zoom Out |	Ctrl+Scroll Wheel