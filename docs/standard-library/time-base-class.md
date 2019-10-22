---
title: time_base 類別
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: ddaf9905e859c062031940d35adfa2a3393dbb5a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685793"
---
# <a name="time_base-class"></a>time_base 類別

類別可做為類別樣板 time_get facet 的基類，只定義列舉類型 `dateorder` 和此類型的數個常數。

## <a name="syntax"></a>語法

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {
        no_order,
        dmy,
        mdy,
        ymd,
        ydm
    };
    time_base(size_t _Refs = 0)
    ~time_base();
};
```

## <a name="remarks"></a>備註

每個常數特性都會以不同的方式描述，來將日期元件排序。 這些常數如下：

- `no_order` 不指定特定的順序。

- `dmy` 指定訂單 day、month、year，如1979年12月2日。

- `mdy` 指定訂單月份、日、年，如1979年12月2日。

- `ymd` 指定訂單年、月、日，如1979/12/2。

- `ydm` 指定訂單年、日、月，如1979： 2 Dec。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間:** std

## <a name="see-also"></a>請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
