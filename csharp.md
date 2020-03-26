## 'extern' keyword
- The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.
- The `extern` modifier is used to declare a method that is implemented externally. A common use of the extern modifier is with the DllImport attribute when you are using Interop services to call into unmanaged code. In this case, the method must also be declared as static 
