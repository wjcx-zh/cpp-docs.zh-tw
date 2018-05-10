---
title: freelist 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs:
- C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e9a8bf702f4373040a6f7255d67f551b5dbfa60
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="freelist-class"></a>freelist 類別

可管理記憶體區塊的清單。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, class Max>
class freelist
 : public Max
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`Sz`|要配置的陣列元素數目。|
|`Max`|max 類別，表示可在可用清單中儲存的元素數量上限。 max 類別可以是 [max_none](../standard-library/max-none-class.md)、[max_unbounded](../standard-library/max-unbounded-class.md)、[max_fixed_size](../standard-library/max-fixed-size-class.md) 或 [max_variable_size](../standard-library/max-variable-size-class.md)。|

## <a name="remarks"></a>備註

此範本類別會使用清單最大長度 (由傳入 `Max` 的 max 類別所決定)，來管理 `Sz` 大小的記憶體區塊清單。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[freelist](#freelist)|建構類型 `freelist` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[pop](#pop)|從可用清單中移除第一個記憶體區塊。|
|[push](#push)|將記憶體區塊新增至清單中。|

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="freelist"></a>  freelist::freelist

建構類型 `freelist` 的物件。

```cpp
freelist();
```

### <a name="remarks"></a>備註

## <a name="pop"></a>  freelist::pop

從可用清單中移除第一個記憶體區塊。

```cpp
void *pop();
```

### <a name="return-value"></a>傳回值

傳回從清單中移除之記憶體區塊的指標。

### <a name="remarks"></a>備註

如果清單是空的，成員函式會傳回 `NULL`。 否則，會從清單中移除第一個記憶體區塊。

## <a name="push"></a>  freelist::push

將記憶體區塊新增至清單中。

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`ptr`|要新增至可用清單的記憶體區塊指標。|

### <a name="return-value"></a>傳回值

如果 max 類別的 `full` 函式傳回 `false`，即為 `true`；否則 `push` 函式會傳回 `false`。

### <a name="remarks"></a>備註

如果 max 類別的 `full` 函式傳回 `false`，此成員函式會將 `ptr` 所指向的記憶體區塊新增至清單開頭。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
