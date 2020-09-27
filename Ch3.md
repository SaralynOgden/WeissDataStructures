3.1

This is given in figure 3.4 in the chapter.

3.2

A missing/not allowed copy constructor will be detected at compile time. At runtime, missing operator methods needed to run a given template, >> being used at the end of templates within templates, and any error that occurs within a regular class will all be detected.

3.3

In order to use a class template the label `template <class Object>` must be listed at the top of the class. In the implementation of the methods for a class with a template, each must have the form `template<class Object> ReturnType ClassName<Object>::MemberName(Parameter List)`

3.4

```
template <class Object>
Object min(Object & obj1, Object & obj2)
{
  return obj1 < obj2 ? obj1 : obj2;
}

template <class Object>
Object max(Object & obj1, Object & obj2)
{
  return obj1 > obj2 ? obj1 : obj2;
}
```

3.5

```
template <typename T>
const T min(const vector<T> & objVector)
{
  if (objVector.size() == 0) 
  {
    throw invalid_argument("...");
  }
  T minValue = objVector[0];
  for (int i = 1; i < objVector.size(); i++)
  {
    minValue = objVector[i] < minValue ? objVector[i] : minValue;
  }
  return minValue;
}

template <typename T>
const T max(const vector<T> & objVector)
{
  if (objVector.size() == 0) 
  {
    throw invalid_argument("...");
  }
  T maxValue = objVector[0];
  for (int i = 1; i < objVector.size(); i++)
  {
    maxValue = objVector[i] > maxValue ? objVector[i] : maxValue;
  }
  return maxValue;
}
```

3.6

In this case we could write our template something like

```
template <class Object>
bool operator>(Object & lhs, Object & rhs) 
{
  return !(lhs < rhs);
}
```

3.7

```
template <class Object>
class SingleBuffer
{
  public:
    explicit SingleBuffer( const Object & initialValue = Object( ) );
    const Object & get( );
    void put( const Object & obj );

  private:
     Object storedValue;
     bool storingValue;
};

template <class Object>
SingleBuffer<Object>::SingleBuffer( const Object & initialValue )
  : storedValue( initialValue )
{
  storingValue = true;
}


template<class Object>
const Object & SingleBuffer<Object>::get()
{
  if (!storingValue) {
    throw invalid_argument("Not storing a value");
  } else {
    storingValue = false;
    return storedValue;
  }
}

template<class Object>
void SingleBuffer<Object>::put (const Object & obj) {
  if (storingValue) {
    throw invalid_argument("Already storing a value");
  } else {
    storedValue = obj;
    storingValue = true;
  }
}
```
