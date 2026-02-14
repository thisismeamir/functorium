# Introduction

Root is a software framework for data analysis and I/O: a powerful tool to cope with the demanding tasks typical of state of the art scientific data analysis. Among its prominent features are an advanced graphical user interface, ideal for interactive analysis, and interpreter for the C++ programming language, for rapid and efficient prototyping and persistency mechanism for C++ objects, used also to write every year petabytes of data recorded by the Large Hadron Collider experiments.

> *This introductory guide illustrates the main features of ROOT which are relevant for the typical problems of data analysis: input and plotting of data from measurements and fitting of analytical functions.*


# Basics

You can use ROOT interactive shell by writing the command in terminal 

```bash
root
```

The prompt should appear shortly:

```
root [0] 
```

One can easily evaluate mathematical expressions in it.

```c++
root [0] 1+1
(int) 2
root [1] 2 * ( 3+ TMath::Pi()) 
(double) 12.283185
```

Now let’s do something more elaborated. A numerical example with the well known geometrical series:

```cpp
root [6] double x=.5
(double) 0.500000
root [7] int N=30
(int) 30
root [8] double geom_series=0
(double) 0.000000
root [9] for (int i=0;i<N;++i)geom_series+=TMath::Power(x,i)
root [10]  cout << TMath::Abs(geom_series - (1-TMath::Power(x,N-1))/(1-x)) <<endl;
1.86265e-09
```
Here we made a step forward. We even declared variables and used a _for_ control structure. Note that there are some subtle differences between Cling and the standard `C++` language. You do not need the “;” at the end of line in interactive mode.

# Learn C++ at the ROOT Prompt

Behind the ROOT prompt there is an interpreter based on a real compiler toolkit: LLVM. It is therefore possible to exercise many features of `C++` and the standard library. For example in the following snippet we define a lambda function, a vector and we sort it in different ways:

```cpp
root [0] using doubles = std::vector<double>;
root [1] auto pVec = [](const doubles& v){for (auto&& x:v) cout << x << endl;};
root [2] doubles v{0,3,5,4,1,2};
root [3] pVec(v);
0
3
5
4
1
2
root [4] std::sort(v.begin(),v.end());
root [5] pVec(v);
0
1
2
3
4
5
root [6] std::sort(v.begin(),v.end(),[](double a, double b){return a>b;});
root [7] pVec(v);
5
4
3
2
1
0
```

Or for random number generation:

```cpp
root [0] std::default_random_engine generator;
root [1] std::normal_distribution<double> distribution(0.,1.);
root [2] distribution(generator)
(std::normal_distribution<double>::result_type) -1.219658e-01
root [3] distribution(generator)
(std::normal_distribution<double>::result_type) -1.086818e+00
root [4] distribution(generator)
(std::normal_distribution<double>::result_type) 6.842899e-01
```
# Plotting

Using one of ROOT’s powerful classes, here `TF1`,[1](https://root.cern.ch/root/htmldoc/guides/primer/ROOTPrimer.html#fn1) will allow us to display a function of one variable, _x_. Try the following:

```cpp
root [11] TF1 f1("f1","sin(x)/x",0.,10.);
root [12] f1.Draw();
```

`f1` is an instance of a TF1 class, the arguments are used in the constructor; the first one of type string is a name to be entered in the internal ROOT memory management system, the second string type parameter defines the function, here `sin(x)/x`, and the two parameters of type double define the range of the variable _x_. The `Draw()` method, here without any parameters, displays the function in a window which should pop up after you typed the above two lines.

A slightly extended version of this example is the definition of a function with parameters, called `[0]`, `[1]` and so on in the ROOT formula syntax. We now need a way to assign values to these parameters; this is achieved with the method `SetParameter(<parameter_number>,<parameter_value>)` of class `TF1`. Here is an example:

```cpp
root [13] TF1 f2("f2","[0]*sin([1]*x)/x",0.,10.);
root [14] f2.SetParameter(0,1);
root [15] f2.SetParameter(1,1);
root [16] f2.Draw();
```

Of course, this version shows the same results as the initial one. Try playing with the parameters and plot the function again. The class `TF1` has a large number of very useful methods, including integration and differentiation. To make full use of this and other ROOT classes, visit the documentation on the Internet under [https://root.cern/doc/master/](https://root.cern/doc/master/). Formulae in ROOT are evaluated using the class `TFormula`, so also look up the relevant class documentation for examples, implemented functions and syntax.