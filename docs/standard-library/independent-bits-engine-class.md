---
title: independent_bits_engine 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 28c9301d270ef516a1acc59f6ab06f0e61a1c9c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687934"
---
# <a name="independent_bits_engine-class"></a>independent_bits_engine 類別

重新封裝基底引擎所傳回值的位元，以產生具有指定位元數的隨機一連串數字。

## <a name="syntax"></a>語法

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>參數

*引擎*\
基底引擎類型。

*W* \
**字組大小**。 每個所產生數字的大小 (位元)。 **前置條件：** `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType* \
不帶正負號的整數結果類型。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。

## <a name="members"></a>Members

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

如需引擎成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>備註

此類別樣板描述*引擎適配*卡，其會從其基底引擎傳回的值中重新封裝位來產生值，並產生*W*位值。

## <a name="requirements"></a>需求

**標頭：** \<random>

**命名空間:** std

## <a name="see-also"></a>請參閱

[\<random>](../standard-library/random.md)
