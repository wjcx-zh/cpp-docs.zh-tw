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
ms.openlocfilehash: 49841d0527d82bf5877322a7c4dab17e95a3360e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846195"
---
# <a name="shuffle_order_engine-class"></a>shuffle_order_engine 類別

透過重新排列基底引擎傳回的值產生隨機序列。

## <a name="syntax"></a>語法

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>參數

*發動機*\
基底引擎類型。

*K*\
**資料表大小**。 緩衝區 (資料表) 中的項目數。 **前置條件**： `0 < K`

## <a name="members"></a>成員

`shuffle_order_engine::shuffle_order_engine`\
`shuffle_order_engine::base`\
`shuffle_order_engine::base_type`\
`shuffle_order_engine::discard`\
`shuffle_order_engine::operator()`\
`shuffle_order_engine::seed`

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>備註

此類別樣板描述可透過重新排列其基底引擎所傳回的值來產生值的 *引擎適配* 卡。 每個函式都會以基底引擎所傳回的 *K* 值填滿內部資料表，並在要求值時從資料表中選取隨機元素。

## <a name="requirements"></a>規格需求

**標頭：**\<random>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
