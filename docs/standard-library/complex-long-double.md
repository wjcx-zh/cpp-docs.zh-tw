---
title: complex&lt;long double&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
dev_langs:
- C++
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 083ef4cea345e7b600782c09a7bdfdc09b4af3d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844669"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

描述可儲存皆為 `long double` 類型之物件的有序對，第一個代表複數的實部，而第二個代表虛部。

## <a name="syntax"></a>語法

```cpp
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);
// rest same as template class complex
};
```

### <a name="parameters"></a>參數

`_RealVal` 型別的值**長雙精度**的建構中複數實部。

`_ImagVal` 型別的值`long double`建構中複數的虛數部分。

`complexNum` 類型的複數**double**或型別**float**其實部及虛部用於初始化類型的複數`long double`所建構。

## <a name="return-value"></a>傳回值

`long double` 類型的複數。

## <a name="remarks"></a>備註

針對 `long double` 類型的複數類別之複數範本類別明確特製化，和此範本類別的差異只在於其定義的建構函式。 允許從 `long double` 到 **float** 的隱含轉換，但從 **double** 轉換成 `long double` 必須是**明確**的。 在**明確**使用的情況下，就無法利用指派語法將類型轉換初始化。

如需 `complex` 範本類別的詳細資訊，請參閱 [complex 類別](../standard-library/complex-class.md)。 如需範本類別 `complex` 的成員清單，請參閱

## <a name="example"></a>範例

```cpp
// complex_comp_ld.cpp
// compile with: /EHsc
#include <complex>
#include <iostream>

int main( )
{
   using namespace std;
   double pi = 3.14159265359;

   // The first constructor specifies real & imaginary parts
   complex <long double> c1 ( 4.0 , 5.0 );
   cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

   // The second constructor initializes values of the real &
   // imaginary parts using those of complex number of type float
   complex <float> c2float ( 1.0 , 3.0 );
   complex <long double> c2longdouble ( c2float );
   cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type double
   complex <double> c3double ( 3.0 , 4.0 );
   complex <long double> c3longdouble ( c3double );
   cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3longdouble );
   double argc3 = arg ( c3longdouble );
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
\* Output:
Specifying initial real & imaginary parts,
 as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
 gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
 gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5
Argument of c3 is recovered from c3 using:
 arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.
*\
```

## <a name="requirements"></a>需求

**標頭**：\<complex>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[complex 類別](../standard-library/complex-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
