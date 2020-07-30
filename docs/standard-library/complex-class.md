---
title: complex 類別
ms.date: 03/27/2019
f1_keywords:
- complex/std::complex::value_type
- complex/std::complex::imag
- complex/std::complex::real
helpviewer_keywords:
- std::complex [C++], value_type
- std::complex [C++], imag
- std::complex [C++], real
ms.assetid: d6492e1c-5eba-4bc5-835b-2a88001a5868
ms.openlocfilehash: db2f8b2f889d9454db737cf5b2a39b414f1d67f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230087"
---
# <a name="complex-class"></a>complex 類別

類別樣板描述一個物件，它會儲存兩個類型的物件 `Type` ，一個代表複數的實數部分，另一個代表虛數部分。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class complex
```

## <a name="remarks"></a>備註

類別的物件 `Type` ：

- 具有公用預設建構函式、解構函式、複製建構函式和指派運算子，且這些都具有傳統行為。

- 可指派整數或浮點值，或轉換類型為具有傳統行為的值。

- 可視需要定義算術運算子和數學函式，將其定義為具有傳統行為的浮點類型。

特別是在指派之後，細微的差異可能不存在於複製建構和預設建構之間。 類別物件的任何作業都 `Type` 不會擲回例外狀況。

這三個浮點類型的類別樣板的明確特製化存在。 在此執行中，任何其他類型的值 `Type` 會轉換為 **`double`** 進行實際計算，並將 **`double`** 結果指派回類型的預存物件 `Type` 。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[複雜化](#complex)|建構具有指定實數與虛數部分或作為其他一些複數複本的複數。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[value_type](#value_type)|類型，表示用來代表複數之實數和虛數部分的資料類型。|

### <a name="functions"></a>函式

|||
|-|-|
|[imag](#imag)|擷取複數的虛數部分。|
|[real](#real)|擷取複數的實數部分。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算子 * =](#op_star_eq)|將目標複數乘以某個因數，該因數可能是複雜類型，或者是與複數的實數和虛數部分相同的類型。|
|[運算子 + =](#op_add_eq)|將目標複數加上某個數字，此加數可能是複雜類型，或者是與複數被加數的實數和虛數部分相同的類型。|
|[operator-=](#operator-_eq)|將目標複數減去某個數字，此減數可能是複雜類型，或者是與複數被減數的實數和虛數部分相同的類型。|
|[operator/=](#op_div_eq)|將目標複數除以某個除數，該除數可能是複雜類型，或者是與複數的實數和虛數部分相同的類型。|
|[operator =](#op_eq)|將目標複數指派某個數字，這個指派的數字可能是複雜類型，或者是與目標複數的實數和虛數部分相同的類型。|

## <a name="complex"></a><a name="complex"></a>複雜化

建構具有指定實數與虛數部分或作為其他一些複數複本的複數。

```cpp
constexpr complex(
    const T& _RealVal = 0,
    const T& _ImagVal = 0);

template <class Other>
constexpr complex(
    const complex<Other>& complexNum);
```

### <a name="parameters"></a>參數

*_RealVal*\
用於初始化建構中複數之實數部分的值。

*_ImagVal*\
用於初始化建構中複數之虛數部分的值。

*complexNum*\
其實數及虛數用於初始化建構中之複數的複數。

### <a name="remarks"></a>備註

第一個函式會將儲存的實數部分初始化至* \_ RealVal* ，並將儲存的虛數部分初始化至* \_ 初始化 imagval*。 第二個函式會將儲存的實數部分初始化為 `complexNum.real()` ，並將儲存的虛數部分初始化為 `complexNum.imag()` 。

在此實作中，若轉譯器不支援成員樣板函式，此樣板：

```cpp
template <class Other>
complex(const complex<Other>& right);
```

取代為：

```cpp
complex(const complex& right);
```

此為複製建構函式。

### <a name="example"></a>範例

```cpp
// complex_complex.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    double pi = 3.14159265359;

    // The first constructor specifies real & imaginary parts
    complex<double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,"
        << "c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of another complex number
    complex<double> c2( c1 );
    cout << "Initializing with the real and imaginary parts of c1,"
        << " c2 = " << c2 << endl;

    // Complex numbers can be initialized in polar form
    // but will be stored in Cartesian form
    complex<double> c3( polar( sqrt( (double)8 ) , pi / 4 ) );
    cout << "c3 = polar( sqrt( 8 ) , pi / 4 ) = " << c3 << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3 );
    double argc3 = arg( c3 );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

## <a name="imag"></a><a name="imag"></a>imag

擷取複數的虛數部分。

```cpp
T imag() const;

T imag(const T& right);
```

### <a name="parameters"></a>參數

*再*\
要擷取其虛數部分的複數。

### <a name="return-value"></a>傳回值

複數的虛數部分。

### <a name="remarks"></a>備註

若為複數*a + bi*，虛數部分或元件為*Im （a + bi） = b*。

### <a name="example"></a>範例

```cpp
// complex_imag.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;

    complex<double> c1( 4.0 , 3.0 );
    cout << "The complex number c1 = " << c1 << endl;

    double dr1 = c1.real();
    cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

    double di1 = c1.imag();
    cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="operator"></a><a name="op_star_eq"></a>運算子 * =

將目標複數乘以某個因數，該因數可能是複雜類型，或者是與複數的實數和虛數部分相同的類型。

```cpp
template <class Other>
complex& operator*=(const complex<Other>& right);

complex<Type>& operator*=(const Type& right);

complex<Type>& operator*=(const complex<Type>& right);
```

### <a name="parameters"></a>參數

*再*\
複數或與目標複數之參數相同類型的數字。

### <a name="return-value"></a>傳回值

複數，其已乘以指定的參數數字。

### <a name="remarks"></a>備註

系統會將運算多載以執行簡單的算數運算，而無須將資料轉換成特定格式。

### <a name="example"></a>範例

```cpp
// complex_op_me.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main()
{
    using namespace std;
    double pi = 3.14159265359;

    // Example of the first member function
    // type complex<double> multiplied by type complex<double>
    complex<double> cl1( polar ( 3.0 , pi / 6 ) );
    complex<double> cr1( polar ( 2.0 , pi / 3 ) );
    cout << "The left-side complex number is cl1 = " << cl1 << endl;
    cout << "The right-side complex number is cr1 = " << cr1 << endl;

    complex<double> cs1 = cl1 * cr1;
    cout << "Quotient of two complex numbers is: cs1 = cl1 * cr1 = "
        << cs1 << endl;

    // This is equivalent to the following operation
    cl1 *= cr1;
    cout << "Quotient of two complex numbers is also: cl1 *= cr1 = "
        << cl1 << endl;

    double abscl1 = abs ( cl1 );
    double argcl1 = arg ( cl1 );
    cout << "The modulus of cl1 is: " << abscl1 << endl;
    cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

    // Example of the second member function
    // type complex<double> multiplied by type double
    complex<double> cl2 ( polar ( 3.0 , pi / 6 ) );
    double cr2 = 5.0;
    cout << "The left-side complex number is cl2 = " << cl2 << endl;
    cout << "The right-side complex number is cr2 = " << cr2 << endl;

    complex<double> cs2 = cl2 * cr2;
    cout << "Quotient of two complex numbers is: cs2 = cl2 * cr2 = "
        << cs2 << endl;

    // This is equivalent to the following operation
    cl2 *= cr2;
    cout << "Quotient of two complex numbers is also: cl2 *= cr2 = "
        << cl2 << endl;

    double abscl2 = abs ( cl2 );
    double argcl2 = arg ( cl2 );
    cout << "The modulus of cl2 is: " << abscl2 << endl;
    cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl;
}
```

## <a name="operator"></a><a name="op_add_eq"></a>運算子 + =

將目標複數加上某個數字，此加數可能是複雜類型，或者是與複數被加數的實數和虛數部分相同的類型。

```cpp
template <class Other>
complex<Type>& operator+=(const complex<Other>& right);

complex<Type>& operator+=(const Type& right);

complex<Type>& operator+=(const complex<Type>& right);
```

### <a name="parameters"></a>參數

*再*\
複數或與目標複數之參數相同類型的數字。

### <a name="return-value"></a>傳回值

複數，其已加上指定的參數數字。

### <a name="remarks"></a>備註

系統會將運算多載以執行簡單的算數運算，而無須將資料轉換成特定格式。

### <a name="example"></a>範例

```cpp
// complex_op_pe.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> added to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 + cr1;
   cout << "The sum of the two complex numbers is: cs1 = cl1 + cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 += cr1;
   cout << "The complex number cr1 added to the complex number cl1 is:"
        << "\n cl1 += cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double added to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 + cr2;
   cout << "The sum of the two complex numbers is: cs2 = cl2 + cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 += cr2;
   cout << "The complex number cr2 added to the complex number cl2 is:"
        << "\n cl2 += cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The sum of the two complex numbers is: cs1 = cl1 + cr1 = (5,3)
The complex number cr1 added to the complex number cl1 is:
cl1 += cr1 = (5,3)
The modulus of cl1 is: 5.83095
The argument of cl1 is: 0.54042 radians, which is 30.9638 degrees.

The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The sum of the two complex numbers is: cs2 = cl2 + cr2 = (3,4)
The complex number cr2 added to the complex number cl2 is:
cl2 += cr2 = (3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 0.927295 radians, which is 53.1301 degrees.
```

## <a name="operator-"></a><a name="operator-_eq"></a>operator-=

將目標複數減去某個數字，此減數可能是複雜類型，或者是與複數被減數的實數和虛數部分相同的類型。

```cpp
template <class Other>
complex<Type>& operator-=(const complex<Other>& complexNum);

complex<Type>& operator-=(const Type& _RealPart);

complex<Type>& operator-=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>參數

*complexNum*\
複數，其為目標複數的減數。

*_RealPart*\
實數，其為目標複數的減數。

### <a name="return-value"></a>傳回值

複數，其已減去指定的參數數字。

### <a name="remarks"></a>備註

系統會將運算多載以執行簡單的算數運算，而無須將資料轉換成特定格式。

### <a name="example"></a>範例

```cpp
// complex_op_se.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> subtracted from type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 - cr1;
   cout << "The difference between the two complex numbers is:"
        << "\n cs1 = cl1 - cr1 = " << cs1 << endl;

   // This is equivalent to the following operation
   cl1 -= cr1;
   cout << "Complex number cr1 subtracted from complex number cl1 is:"
        << "\n cl1 -= cr1 = " << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type double subtracted from type complex<double>
   complex<double> cl2( 2.0 , 4.0 );
   double cr2 = 5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 - cr2;
   cout << "The difference between the two complex numbers is:"
        << "\n cs2 = cl2 - cr2 = " << cs2 << endl;

   // This is equivalent to the following operation
   cl2  -= cr2;
   cout << "Complex number cr2 subtracted from complex number cl2 is:"
        << "\n cl2 -= cr2 = " << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The difference between the two complex numbers is:
cs1 = cl1 - cr1 = (1,5)
Complex number cr1 subtracted from complex number cl1 is:
cl1 -= cr1 = (1,5)
The modulus of cl1 is: 5.09902
The argument of cl1 is: 1.3734 radians, which is 78.6901 degrees.

The left-side complex number is cl2 = (2,4)
The right-side complex number is cr2 = 5
The difference between the two complex numbers is:
cs2 = cl2 - cr2 = (-3,4)
Complex number cr2 subtracted from complex number cl2 is:
cl2 -= cr2 = (-3,4)
The modulus of cl2 is: 5
The argument of cl2 is: 2.2143 radians, which is 126.87 degrees.
```

## <a name="operator"></a><a name="op_div_eq"></a>operator/=

將目標複數除以某個除數，該除數可能是複雜類型，或者是與複數的實數和虛數部分相同的類型。

```cpp
template <class Other>
complex<Type>& operator/=(const complex<Other>& complexNum);

complex<Type>& operator/=(const Type& _RealPart);

complex<Type>& operator/=(const complex<Type>& complexNum);
```

### <a name="parameters"></a>參數

*complexNum*\
複數，其為目標複數的減數。

*_RealPart*\
實數，其為目標複數的減數。

### <a name="return-value"></a>傳回值

複數，其已除以指定的參數數字。

### <a name="remarks"></a>備註

系統會將運算多載以執行簡單的算數運算，而無須將資料轉換成特定格式。

### <a name="example"></a>範例

```cpp
// complex_op_de.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> divided by type complex<double>
   complex<double> cl1( polar (3.0 , pi / 6 ) );
   complex<double> cr1( polar (2.0 , pi / 3 ) );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   complex<double> cs1 = cl1 / cr1;
   cout << "The quotient of the two complex numbers is: cs1 = cl1 /cr1 = "
        << cs1 << endl;

   // This is equivalent to the following operation
   cl1 /= cr1;
   cout << "Quotient of two complex numbers is also: cl1 /= cr1 = "
        << cl1 << endl;

   double abscl1 = abs( cl1 );
   double argcl1 = arg( cl1 );
   cout << "The modulus of cl1 is: " << abscl1 << endl;
   cout << "The argument of cl1 is: "<< argcl1 << " radians, which is "
        << argcl1 * 180 / pi << " degrees." << endl << endl;

   // Example of the second member function
   // type complex<double> divided by type double
   complex<double> cl2( polar(3.0 , pi / 6 ) );
   double cr2 =5;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   complex<double> cs2 = cl2 / cr2;
   cout << "The quotient of the two complex numbers is: cs2 /= cl2 cr2 = "
        << cs2 << endl;

   // This is equivalent to the following operation
   cl2 /= cr2;
   cout << "Quotient of two complex numbers is also: cl2 = /cr2 = "
        << cl2 << endl;

   double abscl2 = abs( cl2 );
   double argcl2 = arg( cl2 );
   cout << "The modulus of cl2 is: " << abscl2 << endl;
   cout << "The argument of cl2 is: "<< argcl2 << " radians, which is "
        << argcl2 * 180 / pi << " degrees." << endl << endl;
}
```

```Output
The left-side complex number is cl1 = (2.59808,1.5)
The right-side complex number is cr1 = (1,1.73205)
The quotient of the two complex numbers is: cs1 = cl1 /cr1 = (1.29904,-0.75)
Quotient of two complex numbers is also: cl1 /= cr1 = (1.29904,-0.75)
The modulus of cl1 is: 1.5
The argument of cl1 is: -0.523599 radians, which is -30 degrees.

The left-side complex number is cl2 = (2.59808,1.5)
The right-side complex number is cr2 = 5
The quotient of the two complex numbers is: cs2 /= cl2 cr2 = (0.519615,0.3)
Quotient of two complex numbers is also: cl2 = /cr2 = (0.519615,0.3)
The modulus of cl2 is: 0.6
The argument of cl2 is: 0.523599 radians, which is 30 degrees.
```

## <a name="operator"></a><a name="op_eq"></a>operator =

將目標複數指派某個數字，這個指派的數字可能是複雜類型，或者是與目標複數的實數和虛數部分相同的類型。

```cpp
template <class Other>
complex<Type>& operator=(const complex<Other>& right);

complex<Type>& operator=(const Type& right);
```

### <a name="parameters"></a>參數

*再*\
複數或與目標複數之參數相同類型的數字。

### <a name="return-value"></a>傳回值

複數，其已指派指定的參數數字。

### <a name="remarks"></a>備註

系統會將運算多載以執行簡單的算數運算，而無須將資料轉換成特定格式。

### <a name="example"></a>範例

```cpp
// complex_op_as.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // Example of the first member function
   // type complex<double> assigned to type complex<double>
   complex<double> cl1( 3.0 , 4.0 );
   complex<double> cr1( 2.0 , -1.0 );
   cout << "The left-side complex number is cl1 = " << cl1 << endl;
   cout << "The right-side complex number is cr1 = " << cr1 << endl;

   cl1  = cr1;
   cout << "The complex number cr1 assigned to the complex number cl1 is:"
        << "\ncl1 = cr1 = " << cl1 << endl;

   // Example of the second member function
   // type double assigned to type complex<double>
   complex<double> cl2( -2 , 4 );
   double cr2 =5.0;
   cout << "The left-side complex number is cl2 = " << cl2 << endl;
   cout << "The right-side complex number is cr2 = " << cr2 << endl;

   cl2 = cr2;
   cout << "The complex number cr2 assigned to the complex number cl2 is:"
        << "\ncl2 = cr2 = " << cl2 << endl;

   cl2 = complex<double>(3.0, 4.0);
   cout << "The complex number (3, 4) assigned to the complex number cl2 is:"
        << "\ncl2 = " << cl2 << endl;
}
```

```Output
The left-side complex number is cl1 = (3,4)
The right-side complex number is cr1 = (2,-1)
The complex number cr1 assigned to the complex number cl1 is:
cl1 = cr1 = (2,-1)
The left-side complex number is cl2 = (-2,4)
The right-side complex number is cr2 = 5
The complex number cr2 assigned to the complex number cl2 is:
cl2 = cr2 = (5,0)
The complex number (3, 4) assigned to the complex number cl2 is:
cl2 = (3,4)
```

## <a name="real"></a><a name="real"></a>即時

取得或設定複數的實數部分。

```cpp
constexpr T real() const;

T real(const T& right);
```

### <a name="parameters"></a>參數

*再*\
要擷取其實數部分的複數。

### <a name="return-value"></a>傳回值

複數的實數部分。

### <a name="remarks"></a>備註

若為複數*a + bi*，實數部分或元件會*重新（a + bi） = a*。

### <a name="example"></a>範例

```cpp
// complex_class_real.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;

   complex<double> c1( 4.0 , 3.0 );
   cout << "The complex number c1 = " << c1 << endl;

   double dr1 = c1.real();
   cout << "The real part of c1 is c1.real() = "
        << dr1 << "." << endl;

   double di1 = c1.imag();
   cout << "The imaginary part of c1 is c1.imag() = "
        << di1 << "." << endl;
}
```

```Output
The complex number c1 = (4,3)
The real part of c1 is c1.real() = 4.
The imaginary part of c1 is c1.imag() = 3.
```

## <a name="value_type"></a><a name="value_type"></a>value_type

類型，表示用來代表複數之實數和虛數部分的資料類型。

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>備註

`value_type`是類別複雜樣板參數的同義字 `Type` 。

### <a name="example"></a>範例

```cpp
// complex_valuetype.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
    using namespace std;
    complex<double>::value_type a = 3, b = 4;

    complex<double> c1 ( a , b );
    cout << "Specifying initial real & imaginary parts"
        << "\nof type value_type: "
        << "c1 = " << c1 << "." << endl;
}
```

```Output
Specifying initial real & imaginary parts
of type value_type: c1 = (3,4).
```

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
