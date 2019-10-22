---
title: complex&lt;double&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<double>
helpviewer_keywords:
- complex<double> function
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
ms.openlocfilehash: 8955669f4bc6fd7b3b373751e0e5134205dd1657
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689783"
---
# <a name="complexltdoublegt"></a>complex&lt;double&gt;

描述一個物件，它會儲存兩個**double**類型之物件的已排序對，第一個代表複數的實數部分，而第二個代表虛數部分。

## <a name="syntax"></a>語法

```cpp
template <>
class complex<double> {
public:
    constexpr complex(
    double RealVal = 0,
    double ImagVal = 0);

constexpr complex(const complex<double>& complexNum);

constexpr explicit complex(const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>參數

*RealVal* \
要建構之複數實數部分的 **double** 類型值。

*初始化 imagval* \
要建構之複數虛數部分的 **double** 類型值。

*complexNum* \
**浮點**類型或類型**long double**的複數，其實際和虛數部分用來初始化所建立之類型**double**的複數。

## <a name="return-value"></a>傳回值

**double** 類型的複數。

## <a name="remarks"></a>備註

對**double**類型的複雜類別而言，類別樣板的明確特製化，不同于類別樣板所定義的函式。 允許從**float**到**double**的轉換是隱含的，但從**long double**轉換成**double**必須是**明確**的。 在**明確**使用的情況下，就無法利用指派語法將類型轉換初始化。

如需類別範本 `complex` 的詳細資訊，請參閱[Complex 類別](../standard-library/complex-class.md)。 如需類別範本的成員清單 `complex`，請參閱。

## <a name="example"></a>範例

```cpp
// complex_comp_dbl.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << "as type double gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 4.0 , 5.0 );
   complex <double> c2double ( c2float );
   cout << "Implicit conversion from type float to type double,"
        << endl << "gives c2double = " << c2double << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 4.0 , 5.0 );
   complex <double> c3double ( c3longdouble );
   cout << "Explicit conversion from type float to type double,"
        << endl << "gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:" << endl
        << "arg ( c3 ) = " << argc3 << " radians, which is "
        << argc3 * 180 / pi << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type double gives c1 = (4,5)
Implicit conversion from type float to type double,
gives c2double = (4,5)
Explicit conversion from type float to type double,
gives c3longdouble = (4,5)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 6.40312
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.896055 radians, which is 51.3402 degrees.
*/
```

## <a name="requirements"></a>需求

**標頭**：\<complex>

**命名空間:** std

## <a name="see-also"></a>請參閱

[complex 類別](../standard-library/complex-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
