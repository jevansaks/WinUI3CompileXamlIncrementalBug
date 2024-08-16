# CompileXaml incremental bug with CppWinRT and multiple namespaces

Repro is to have an IDL with two different top-level namespaces. Then:

1. Modify MainWindow.xaml.cpp (doesn't matter how, just add a space somewhere)
2. Build solution
3. Result, XAML recompiles because "number of assemblies changed"

This is because pass2 gets a reference assembly that pass1 does not, which causes the finger print check to fail every time.

In this repro the extra assembly is `WinUI3CompileXamlIncrementalBug\x64\Debug\WinUI3CompileXamlIncrementalBug\Repro.winmd`.
