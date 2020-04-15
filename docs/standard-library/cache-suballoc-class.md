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
ms.openlocfilehash: 55860a65fc77f834ed699f3a5114768b7efdde6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366724"
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
|*深圳*|所配置陣列中的元素數。|

## <a name="remarks"></a>備註

cache_suballoc類範本將處理位置的記憶體區儲存在具有無界長度的可用清單中,使用`freelist<sizeof(Type), max_unbounded>`,並在空閒清單為空時從與**運算符新**分配的較大塊中分配記憶體區塊。

每個區塊`Sz * Nelts`都保存可用記憶體的位元組以及**運算元新**和**運算元刪除**所需的資料。 永遠不會釋放已配置的區塊。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_suballoc](#cache_suballoc)|建構類型 `cache_suballoc` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[配置](#allocate)|配置記憶體區塊。|
|[去分配](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a>cache_suballoc:分配

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a>cache_suballoc:cache_suballoc

建構類型 `cache_suballoc` 的物件。

```cpp
cache_suballoc();
```

### <a name="remarks"></a>備註

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a>cache_suballoc::d分配

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
