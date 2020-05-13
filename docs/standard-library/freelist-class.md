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
ms.openlocfilehash: 712c1f1638b954d1580eb527dd9eab7401917517
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317198"
---
# <a name="freelist-class"></a>freelist 類別

可管理記憶體區塊的清單。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*深圳*|所配置陣列中的元素數。|
|*麥克斯*|max 類別，表示可在可用清單中儲存的元素數量上限。 max 類別可以是 [max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_fixed_size](../standard-library/max-fixed-size-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>備註

此類範本管理大小*Sz*的記憶體區列,該清單的最大長度由*Max*中傳遞的最大類確定。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[freelist](#freelist)|建構類型 `freelist` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[流行](#pop)|從可用清單中移除第一個記憶體區塊。|
|[推](#push)|將記憶體區塊新增至清單中。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a>自由清單::免費清單

建構類型 `freelist` 的物件。

```cpp
freelist();
```

### <a name="remarks"></a>備註

## <a name="freelistpop"></a><a name="pop"></a>自由清單::pop

從可用清單中移除第一個記憶體區塊。

```cpp
void *pop();
```

### <a name="return-value"></a>傳回值

傳回從清單中移除之記憶體區塊的指標。

### <a name="remarks"></a>備註

如果清單為空,則成員函數傳回 NULL。 否則，會從清單中移除第一個記憶體區塊。

## <a name="freelistpush"></a><a name="push"></a>自由名單::p

將記憶體區塊新增至清單中。

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Ptr*|要新增至可用清單的記憶體區塊指標。|

### <a name="return-value"></a>傳回值

**如果**最大類別`full`函數傳**回 false,** 則為 true ;否則,`push`函數會傳回**false**。

### <a name="remarks"></a>備註

如果`full`max 類的函數傳回**false,** 則此成員函數會將*ptr*指向的記憶體區塊添加到清單的頭部。

## <a name="see-also"></a>另請參閱

[\<配置器>](../standard-library/allocators-header.md)
