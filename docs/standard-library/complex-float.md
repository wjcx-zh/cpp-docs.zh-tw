---
title: complex&lt;float&gt;
ms.date: 11/04/2016
f1_keywords:
- complex/std::complex<float>
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
ms.openlocfilehash: 7b49e63302ad0c26f393fdfd9dd443c77455a643
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688247"
---
# <a name="complexltfloatgt"></a>complex&lt;float&gt;

描述一個物件，它會儲存類型為**float**之物件的已排序對，第一個代表複數的實數部分，而第二個代表虛數部分。

## <a name="syntax"></a>語法

```cpp
template <>
class complex<float> {
public:
    constexpr complex(
    float _RealVal = 0,
    float _ImagVal = 0);

constexpr complex(
    const complex<float>& complexNum);

constexpr complex(
    const complex<double>& complexNum);

constexpr complex(
    const complex<long double>& complexNum);
// rest same as class template complex
};
```

### <a name="parameters"></a>參數

*_RealVal* \
要建構之複數實數部分的 **float** 類型值。

*_ImagVal* \
要建構之複數虛數部分的 **float** 類型值。

*complexNum* \
**Double**類型或類型**長 double**的複數，其實際和虛數部分用來初始化所建立之**float**類型的複數。

## <a name="return-value"></a>傳回值

**float** 類型的複數。

## <a name="remarks"></a>備註

對**float**類型的複雜類別而言，類別樣板的明確特製化，不同于它所定義之函式中的類別樣板。 允許從**float**到**double**的轉換是隱含的，但從**float**到**long double**的較不安全轉換必須是**明確**的。 在**明確**使用的情況下，就無法利用指派語法將類型轉換初始化。

如需類別範本 `complex` 的詳細資訊，請參閱[Complex 類別](../standard-library/complex-class.md)。 如需類別範本的成員清單 `complex`，請參閱。

## <a name="example"></a>範例

```cpp
// complex_comp_flt.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <float> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type double
   complex <double> c2double ( 1.0 , 3.0 );
   complex <float> c2float ( c2double );
   cout << "Implicit conversion from type double to type float,"
        << endl << "gives c2float = " << c2float << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 3.0 , 4.0 );
   complex <float> c3float ( c3longdouble );
   cout << "Explicit conversion from type long double to type float,"
        << endl << "gives c3float = " << c3float << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3float);
   double argc3 = arg ( c3float);
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:"
        << endl << "arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
/* Output:
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type double to type float,
gives c2float = (1,3)
Explicit conversion from type long double to type float,
gives c3float = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*/
```

## <a name="requirements"></a>需求

**標頭**：\<complex>

**命名空間:** std

## <a name="see-also"></a>請參閱

[complex 類別](../standard-library/complex-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
