---
title: cache_suballoc 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ccc01372d08edb997ed6b0aaa70be69fde60a1e2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954319"
---
# <a name="cachesuballoc-class"></a>cache_suballoc 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*sz*|所配置陣列中的元素數。|

## <a name="remarks"></a>備註

Cache_suballoc 樣板類別會儲存已解除配置的記憶體區塊長度的可用清單中使用`freelist<sizeof(Type), max_unbounded>`，和 suballocates 之較大的區塊，以配置的記憶體區塊**new 運算子**時可用的清單空的。

每個區塊會保留`Sz * Nelts`個位元組的可用記憶體，以及資料的**new 運算子**並**運算子 delete**需要。 永遠不會釋放已配置的區塊。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_suballoc](#cache_suballoc)|建構類型 `cache_suballoc` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="allocate"></a>  cache_suballoc::allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*count*|所配置陣列中的元素數。|

### <a name="return-value"></a>傳回值

所配置物件的指標。

### <a name="remarks"></a>備註

## <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc

建構類型 `cache_suballoc` 的物件。

```cpp
cache_suballoc();
```

### <a name="remarks"></a>備註

## <a name="deallocate"></a>  cache_suballoc::deallocate

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|要從儲存體解除配置之第一個物件的指標。|
|*count*|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
