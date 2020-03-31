## 'extern' keyword
- The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.
- The `extern` modifier is used to declare a method that is implemented externally. A common use of the extern modifier is with the DllImport attribute when you are using Interop services to call into unmanaged code. In this case, the method must also be declared as static 


## Usage of PDB File
- A file with the `.PDB` file extension is a file created in the Program Database format that is used to hold debugging information about a program or module, like a DLL or EXE file.


## Extension Methods
- Extension methods enable you to "add" methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type. 
- Extension methods are static methods, but they're called as if they were instance methods on the extended type.

```csharp
namespace ExtensionMethods
{
    public static class MyExtensions
    {
        public static int WordCount(this String str)
        {
            return str.Split(new char[] { ' ', '.', '?' }, 
                             StringSplitOptions.RemoveEmptyEntries).Length;
        }
    }   
}
```
Use the above extension as below...
```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```
