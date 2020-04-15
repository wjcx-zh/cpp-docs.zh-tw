---
title: cache_chunklist 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: d0dd6176a34bd625069511106c491225d1467d08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366748"
---
# <a name="cache_chunklist-class"></a>cache_chunklist 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*深圳*|所配置陣列中的元素數。|

## <a name="remarks"></a>備註

類範本使用**新運算元**來分配原始記憶體塊,根據需要為記憶體區塊分配存儲的子分配塊;它將處理的記憶體儲存在每個塊的單獨可用清單中,並使用**運算符刪除**在其記憶體區塊未使用時解分配區塊。

每個記憶體區都保存可用記憶體的*Sz*位元組和指向其所屬塊的指標。 每個塊包含`Nelts`記憶體塊、三個指標、int 以及**操作員新**資料和**運算符刪除**所需的數據。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_chunklist](#cache_chunklist)|建構類型 `cache_chunklist` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[配置](#allocate)|配置記憶體區塊。|
|[去分配](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a>cache_chunklist:分配

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a>cache_chunklist:cache_chunklist

建構類型 `cache_chunklist` 的物件。

```cpp
cache_chunklist();
```

### <a name="remarks"></a>備註

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a>cache_chunklist::d分配

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Ptr*|要從儲存空間解除配置之第一個物件的指標。|
|*count*|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<配置器>](../standard-library/allocators-header.md)
