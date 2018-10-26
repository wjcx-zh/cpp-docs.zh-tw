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
ms.openlocfilehash: e1d17b66285b60190a5c91c8defd5adf51f79a6a
ms.sourcegitcommit: 8c2de32e96c84d0147af3cce1e89e4f28707ff12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143649"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

此明確特製化的範本類別描述可儲存已排序的配對的物件，這兩個型別**長雙精度**，第一個代表第二個複數的實數部分代表虛數部分。

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

*_RealVal*<br/>
要建構之複數實數部分的 **long double** 類型值。

*_ImagVal*<br/>
類型的值**長雙精度**的建構中複數之虛數部分。

*complexNum*<br/>
類型的複數**雙**或型別的**float**其實部及虛部用於初始化類型的複數**長雙精度**所建構。

## <a name="return-value"></a>傳回值

類型的複數**長雙精度**。

## <a name="remarks"></a>備註

此範本類別明確特製化`complex`複雜類型類別之**長雙精度**不同於樣板類別，只在它所定義的建構函式中。 從轉換**長雙精度**來**float**允許隱含的但從轉換**double**至**長雙精度**需要要**明確**。 在**明確**使用的情況下，就無法利用指派語法將類型轉換初始化。

如需有關此範本類別`complex`和其成員，請參閱[complex 類別](../standard-library/complex-class.md)。

**Microsoft 專有**:**長雙精度**並**double**類型有相同表示法，但是不同的類型。 如需詳細資訊，請參閱 <<c0> [ 基本類型](../cpp/fundamental-types-cpp.md)。

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
    complex<long double> c1( 4.0 , 5.0 );
    cout << "Specifying initial real & imaginary parts,\n"
        << " as type float gives c1 = " << c1 << endl;

    // The second constructor initializes values of the real &
    // imaginary parts using those of complex number of type float
    complex<float> c2float( 1.0 , 3.0 );
    complex<long double> c2longdouble ( c2float );
    cout << "Implicit conversion from type float to type long double,"
        << "\n gives c2longdouble = " << c2longdouble << endl;

    // The third constructor initializes values of the real &
    // imaginary parts using those of a complex number
    // of type double
    complex<double> c3double( 3.0 , 4.0 );
    complex<long double> c3longdouble( c3double );
    cout << "Implicit conversion from type long double to type float,"
        << "\n gives c3longdouble = " << c3longdouble << endl;

    // The modulus and argument of a complex number can be recovered
    double absc3 = abs( c3longdouble );
    double argc3 = arg( c3longdouble );
    cout << "The modulus of c3 is recovered from c3 using: abs( c3 ) = "
        << absc3 << endl;
    cout << "Argument of c3 is recovered from c3 using:\n arg( c3 ) = "
        << argc3 << " radians, which is " << argc3 * 180 / pi
        << " degrees." << endl;
}
```

```Output
Specifying initial real & imaginary parts,
as type float gives c1 = (4,5)
Implicit conversion from type float to type long double,
gives c2longdouble = (1,3)
Implicit conversion from type long double to type float,
gives c3longdouble = (3,4)
The modulus of c3 is recovered from c3 using: abs( c3 ) = 5
Argument of c3 is recovered from c3 using:
arg( c3 ) = 0.927295 radians, which is 53.1301 degrees.
```

## <a name="requirements"></a>需求

**標頭**：\<complex>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[complex 類別](../standard-library/complex-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
