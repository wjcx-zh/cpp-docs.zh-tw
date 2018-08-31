---
title: complex&lt;float&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- complex/std::complex<float>
dev_langs:
- C++
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf266e11f975e3ce01e5359c1dac65b46a42435a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221339"
---
# <a name="complexltfloatgt"></a>complex&lt;float&gt;

描述可儲存型別之物件的排序的配對**浮點數**，第一個代表第二個複數的實數部分代表虛數部分。

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
// rest same as template class complex
};
```

### <a name="parameters"></a>參數

*_RealVal*<br/>
要建構之複數實數部分的 **float** 類型值。

*_ImagVal*<br/>
要建構之複數虛數部分的 **float** 類型值。

*complexNum*<br/>
類型的複數**雙**或型別的**長雙精度**其實部及虛部用於初始化類型的複數**float**所建構。

## <a name="return-value"></a>傳回值

**float** 類型的複數。

## <a name="remarks"></a>備註

**float** 類型 complex 類別的 complex 範本類別明確特製化，其與範本類別的差異只在於所定義的建構函式。 從轉換**浮點數**來**double**允許隱含的但較不安全的轉換，從**float**至**長雙精度**是一定要**明確**。 在**明確**使用的情況下，就無法利用指派語法將類型轉換初始化。

如需 `complex` 範本類別的詳細資訊，請參閱 [complex 類別](../standard-library/complex-class.md)。 如需範本類別 `complex` 的成員清單，請參閱

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
        << "\n gives c2float = " << c2float << endl;

   // The third constructor initializes values of the real &
   // imaginary parts using those of a complex number
   // of type long double
   complex <long double> c3longdouble ( 3.0 , 4.0 );
   complex <float> c3float ( c3longdouble );
   cout << "Explicit conversion from type long double to type float,"
        << "\n gives c3float = " << c3float << endl;

   // The modulus and argument of a complex number can be recovered
   double absc3 = abs ( c3float);
   double argc3 = arg ( c3float);
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "
        << absc3 << endl;
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
\* Output:
Specifying initial real & imaginary parts,
 as type float gives c1 = (4,5)
Implicit conversion from type double to type float,
 gives c2float = (1,3)
Explicit conversion from type long double to type float,
 gives c3float = (3,4)
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
