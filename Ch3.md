3.1


3.2

A missing/not allowed copy constructor will be detected at compile time. At runtime, missing operator methods needed to run a given template, >> being used at the end of templates within templates, and any error that occurs within a regular class will all be detected.

3.3

In order to use a class template the label `template <class Object>` must be listed at the top of the class. In the implementation of the methods for a class with a template, each must have the form `template<class Object> ReturnType ClassName<Object>::MemberName(Parameter List)`

3.4


3.6

In this case we could write our template something like

```
template <class Object>
bool operator>(Object & lhs, Object & rhs) {
  return !(lhs < rhs);
}
```

3.7
