---
title: freelist 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: bf88e33f5d00b9b6b90d2712a0bbabaa3e571340
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561202"
---
# <a name="freelist-class"></a>freelist 類別

可管理記憶體區塊的清單。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>參數

*深圳*\
所配置陣列中的元素數。

*麥克斯*\
max 類別，表示可在可用清單中儲存的元素數量上限。 max 類別可以是 [max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_fixed_size](../standard-library/max-fixed-size-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。

## <a name="remarks"></a>備註

這個類別樣板會以最大的最大值 *（最大*值）所決定清單的最大長度，來管理以*Sz*為大小的記憶體區塊清單。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[freelist](#freelist)|建構類型 `freelist` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[流行](#pop)|從可用清單中移除第一個記憶體區塊。|
|[push](#push)|將記憶體區塊新增至清單中。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a> freelist：： freelist

建構類型 `freelist` 的物件。

```cpp
freelist();
```

### <a name="remarks"></a>備註

## <a name="freelistpop"></a><a name="pop"></a> freelist：:p op

從可用清單中移除第一個記憶體區塊。

```cpp
void *pop();
```

### <a name="return-value"></a>傳回值

傳回從清單中移除之記憶體區塊的指標。

### <a name="remarks"></a>備註

如果清單是空的，則成員函式會傳回 Null。 否則，會從清單中移除第一個記憶體區塊。

## <a name="freelistpush"></a><a name="push"></a> freelist：:p ush

將記憶體區塊新增至清單中。

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>參數

*Ptr*\
要新增至可用清單的記憶體區塊指標。

### <a name="return-value"></a>傳回值

**`true`** 如果 max 類別的函式傳回，則為 `full` **`false`** ，否則 `push` 函數會傳回 **`false`** 。

### <a name="remarks"></a>備註

如果 max 類別的函式傳回 `full` **`false`** ，此成員函式會將 *ptr* 所指向的記憶體區塊新增至清單的開頭。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
