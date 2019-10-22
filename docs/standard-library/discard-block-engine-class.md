---
title: discard_block_engine 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: eb00945084affb2be9299953e5ca9352c56d3b32
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688098"
---
# <a name="discard_block_engine-class"></a>discard_block_engine 類別

捨棄其基底引擎所傳回的值，以產生隨機序列。

## <a name="syntax"></a>語法

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>參數

*引擎*\
基底引擎類型。

*P* \
**區塊大小**。 每個區塊中的值數目。

*R*\
**已使用的區塊**。 每個區塊中使用的值數目。 其餘部分會被捨棄（`P`  -  `R`）。 **前置條件：** `0 < R ≤ P`

## <a name="members"></a>Members

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>備註

此類別範本會藉由捨棄其基底引擎所傳回的一些值來描述產生值的引擎介面卡。

## <a name="requirements"></a>需求

**標頭：** \<random>

**命名空間:** std

## <a name="see-also"></a>請參閱

[\<random>](../standard-library/random.md)
