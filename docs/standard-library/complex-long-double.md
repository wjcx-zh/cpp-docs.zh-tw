---
title: complex&lt;long double&gt;
ms.date: 11/04/2016
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
ms.openlocfilehash: 73027ba76d608424b1a6da346e861b10c66989fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228384"
---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;

這個明確特製化的類別樣板描述一個物件，它會儲存一組已排序的物件，這兩個類型都是 **`long double`** ，第一個代表複數的實數部分，而第二個代表虛數部分。

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

// rest same as class template complex
};
```

### <a name="parameters"></a>參數

*_RealVal*\
**`long double`** 所要建立之複數實數部分的類型值。

*_ImagVal*\
**`long double`** 所要建立之複數虛數部分的類型值。

*complexNum*\
類型 **`double`** 或類型的複數， **`float`** 其實際和虛數部分是用來初始化所要建立之類型的 **`long double`** 複數。

## <a name="return-value"></a>傳回值

類型的複數 **`long double`** 。

## <a name="remarks"></a>備註

類別樣板對類型的複雜類別的明確特製化， `complex` **`long double`** 與類別樣板僅限於它所定義的函式。 從轉換 **`long double`** 成 **`float`** 是允許隱含的，但從到的轉換必須 **`double`** 是 **`long double`** **`explicit`** 。 使用規則時，會使用 **`explicit`** 指派語法來進行類型轉換。

如需類別範本及其成員的詳細資訊 `complex` ，請參閱[complex 類別](../standard-library/complex-class.md)。

**Microsoft 特有**： **`long double`** 和 **`double`** 類型具有相同的標記法，但為不同的類型。 如需詳細資訊，請參閱[內建類型](../cpp/fundamental-types-cpp.md)。

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

[complex 類別](../standard-library/complex-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
