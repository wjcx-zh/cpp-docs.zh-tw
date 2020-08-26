---
title: random_device 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
ms.openlocfilehash: b2176ce7dcdefdcf4fc0846cd18b1b01d4de2916
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843543"
---
# <a name="random_device-class"></a>random_device 類別

從外部裝置產生隨機序列。

## <a name="syntax"></a>語法

```cpp
class random_device {
public:
   typedef unsigned int result_type;

   // constructor
   explicit random_device(const std::string& token = "");

   // properties
   static result_type min();
   static result_type max();
   double entropy() const;

   // generate
   result_type operator()();

   // no-copy functions
   random_device(const random_device&) = delete;
   void operator=(const random_device&) = delete;
   };
```

## <a name="members"></a>成員

[random_device](#random_device)\
[熵](#entropy)\
[random_device::operator()](#op_call)

## <a name="remarks"></a>備註

此類別會描述亂數的來源，且允許 (但不一定需要) 是不具決定性，或是由 ISO C++ 標準以密碼編譯保護。 在 Visual Studio 實作中，產生的值是不具決定性且以密碼編譯保護，但執行速度比從引擎及引擎配接器 (例如 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)，對大多數應用程式而言是高品質且快速的引擎選擇) 建立的產生器更慢。

`random_device` 結果會統一分佈在接近的範圍 [ `0, 2`<sup>32</sup>) 中。

`random_device` 不保證會產生未封鎖的呼叫。

一般而言，會使用 `random_device` 植入使用引擎或引擎配接器建立的其他產生器。 如需詳細資訊，請參閱 [\<random>](../standard-library/random.md)。

## <a name="example"></a>範例

下列程式碼示範此類別的基本功能及範例結果。 因為 `random_device` 的不具決定性特質，顯示在「輸出」**** 區段中的隨機值不會與您的結果相符。 這是正常且符合預期的。

```cpp
// random_device_engine.cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <random>
#include <iostream>
using namespace std;

int main()
{
    random_device gen;

    cout << "entropy == " << gen.entropy() << endl;
    cout << "min == " << gen.min() << endl;
    cout << "max == " << gen.max() << endl;

    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
}
```

```Output
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```

這是針對此產生器的最簡化範例，不代表一般使用情況。 如需更具代表性的程式碼範例，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="requirements"></a>規格需求

**標頭：**\<random>

**命名空間：** std

## <a name="random_devicerandom_device"></a><a name="random_device"></a> random_device：： random_device

建構產生器。

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>備註

建構函式會視需要初始化產生器，忽略字串參數。 若無法初始化 `random_device`，會擲出衍生自 [exception](../standard-library/exception-class.md) 之實作定義類型的值。

## <a name="random_deviceentropy"></a><a name="entropy"></a> random_device：：熵

評估來源的隨機性。

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>備註

成員函式會傳回來源隨機性的評估 (測量單位為位元)。

## <a name="random_deviceoperator"></a><a name="op_call"></a> random_device：： operator ( # A1

傳回隨機值。

```cpp
result_type operator()();
```

### <a name="remarks"></a>備註

傳回統一分佈在封閉間隔 [`min, max`] 中的值，而此間隔是透過成員函式 `min()` 和 `max()` 所決定。 如果無法取得亂數，會擲回衍生自 [exception](../standard-library/exception-class.md) 之實作定義類型的值。

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
