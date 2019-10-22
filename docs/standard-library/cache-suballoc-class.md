---
title: cache_suballoc 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: 7a21f0c4f81277200ff069baf751fa013a3c0cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688350"
---
# <a name="cache_suballoc-class"></a>cache_suballoc 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Sz*|陣列中要配置的項目數。|

## <a name="remarks"></a>備註

Cache_suballoc 類別樣板會將已解除配置的記憶體區塊儲存在具有不受限制長度的可用清單中，並使用 `freelist<sizeof(Type), max_unbounded>`，並從使用**operator new**所配置的較大區塊 suballocates 記憶體區塊（當可用清單是空的時）。

每個區塊都包含 `Sz * Nelts` 個位元組的可用記憶體，以及**operator new**和**operator delete**所需的資料。 永遠不會釋放已配置的區塊。

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

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="allocate"></a>  cache_suballoc::allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*count*|陣列中要配置的項目數。|

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

## <a name="see-also"></a>請參閱

[\<allocators>](../standard-library/allocators-header.md)
