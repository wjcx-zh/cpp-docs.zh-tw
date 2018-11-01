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
ms.openlocfilehash: bf767c12a19e4ae47c34a8f01e1b1a2f1e028eb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676651"
---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine 類別

透過重新排列基底引擎傳回的值產生隨機序列。

## <a name="syntax"></a>語法

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>參數

*引擎*<br/>
基底引擎類型。

*K*<br/>
**資料表大小**。 緩衝區 (資料表) 中的項目數。 **前置條件**：`0 < K`

## <a name="members"></a>成員

||||
|-|-|-|
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>備註

此範例類別描述「引擎配接器」，會透過重新排列其基底引擎所傳回的值來產生值。 每個建構函式會將內部資料表填滿*K*基底引擎所傳回的值和值，要求時從資料表選取隨機項目。

## <a name="requirements"></a>需求

**標頭：**\<random>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)<br/>
