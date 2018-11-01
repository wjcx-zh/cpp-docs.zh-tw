---
title: chrono 常值
ms.date: 11/04/2016
ms.assetid: 1a9e23b1-256f-4570-8226-5fa7364fb032
ms.openlocfilehash: 838ae99f5a21660968e0215818aa959348f38305
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494727"
---
# <a name="chrono-literals"></a>chrono 常值

(C++14) \<chrono> 標頭定義 12 個[使用者定義常值](../cpp/user-defined-literals-cpp.md)，來加速使用代表小時、分鐘、秒、毫秒、百萬分之一秒及奈秒的常值。 每個使用者定義常值皆有整數和浮點多載。 常值在 literals::chrono_literals 內嵌命名空間中定義，當 std::chrono 在範圍中時會自動將此內嵌命名空間帶入範圍內。

## <a name="syntax"></a>語法

```cpp
inline namespace literals {
  inline namespace chrono_literals {
    // return integral hours
    constexpr chrono::hours operator"" h(unsigned long long Val);

    // return floating-point hours
    constexpr chrono::duration<double, ratio<3600>> operator"" h(long double Val);

    // return integral minutes
    constexpr chrono::minutes(operator"" min)(unsigned long long Val);

    // return floating-point minutes
    constexpr chrono::duration<double, ratio<60>>(operator"" min)(long double Val);

    // return integral seconds
    constexpr chrono::seconds operator"" s(unsigned long long Val);

    // return floating-point seconds
    constexpr chrono::duration<double> operator"" s(long double Val);

    // return integral milliseconds
    constexpr chrono::milliseconds operator"" ms(unsigned long long Val);

    // return floating-point milliseconds
    constexpr chrono::duration<double, milli> operator"" ms(long double Val);

    // return integral microseconds
    constexpr chrono::microseconds operator"" us(unsigned long long Val);

    // return floating-point microseconds
    inline constexpr chrono::duration<double, micro> operator"" us(long double Val);

    // return integral nanoseconds
    inline constexpr chrono::nanoseconds operator"" ns(unsigned long long Val);

    // return floating-point nanoseconds
    constexpr chrono::duration<double, nano> operator"" ns(long double Val);

  } // inline namespace chrono_literals
} // inline namespace literals
```

## <a name="return-value"></a>傳回值

需要的常值**long long**引數傳回值或對應的型別。 接受浮點引數的常值會傳回 [duration](../standard-library/duration-class.md)。

## <a name="example"></a>範例

下列範例顯示如何使用 chrono 常值。

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="requirements"></a>需求

**標頭**：\<chrono>

**命名空間**：std::literals::chrono_literals

## <a name="see-also"></a>另請參閱

[\<chrono>](../standard-library/chrono.md)<br/>
