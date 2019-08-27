---
title: time_base 類別
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: 85565dc0c0ec904551eb8dd981cfacc9a2e1f256
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460044"
---
# <a name="timebase-class"></a>time_base 類別

類別可做為樣板類別 time_get facet 的基類, 只定義列舉類型`dateorder`和此類型的數個常數。

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

- `no_order`不指定特定的順序。

- `dmy`指定訂單 day、month、year, 如1979年12月2日。

- `mdy`以1979年12月2日的順序指定訂單月份、日、年。

- `ymd`指定訂單年、月、日, 如1979/12/2。

- `ydm`指定訂單 year、day、then month, 如1979所示:12月2日。

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
