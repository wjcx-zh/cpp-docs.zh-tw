---
title: shuffle_order_engine 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
helpviewer_keywords:
- std::shuffle_order_engine [C++]
- std::shuffle_order_engine [C++], base
- std::shuffle_order_engine [C++], discard
- std::shuffle_order_engine [C++], base_type
- std::shuffle_order_engine [C++], seed
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
ms.openlocfilehash: 972ba83afb5478cd89314817ba823b8d5657c9c8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450419"
---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine 類別

透過重新排列基底引擎傳回的值產生隨機序列。

## <a name="syntax"></a>語法

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>參數

*搜尋引擎優化*\
基底引擎類型。

*K*\
**資料表大小**。 緩衝區 (資料表) 中的項目數。 **前置條件**：`0 < K`

## <a name="members"></a>成員

||||
|-|-|-|
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>備註

此範例類別描述「引擎配接器」，會透過重新排列其基底引擎所傳回的值來產生值。 每個函式都會使用基底引擎傳回的*K*值來填滿內部資料表, 而在要求值時, 會從資料表中選取隨機元素。

## <a name="requirements"></a>需求

**標頭：** \<random>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
