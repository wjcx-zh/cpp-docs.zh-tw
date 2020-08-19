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
ms.openlocfilehash: 1ee422423356a18f1c81796790593a20dc03fbab
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560709"
---
# <a name="cache_chunklist-class"></a>cache_chunklist 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>參數

*深圳*\
所配置陣列中的元素數。

## <a name="remarks"></a>備註

這個類別樣板使用 **new 運算子** 來配置未經處理記憶體的區塊，並在需要時為記憶體區塊配置儲存體 suballocating 區塊;它會將解除配置的記憶體區塊儲存在每個區塊的個別可用清單中，並在沒有任何記憶體區塊正在使用時，使用 **operator delete** 來解除配置區塊。

每個記憶體區塊都會保存可使用記憶體的 *Sz* 位元組，以及其所屬區塊的指標。 每個區塊都 `Nelts` 有記憶體區塊、三個指標、int 以及 **運算子 new** 和 **operator delete** 所需的資料。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_chunklist](#cache_chunklist)|建構類型 `cache_chunklist` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[解除](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a> cache_chunklist：： allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

*計數*\
所配置陣列中的元素數。

### <a name="return-value"></a>傳回值

所配置物件的指標。

### <a name="remarks"></a>備註

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a> cache_chunklist：： cache_chunklist

建構類型 `cache_chunklist` 的物件。

```cpp
cache_chunklist();
```

### <a name="remarks"></a>備註

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a> cache_chunklist：:d eallocate

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>參數

*Ptr*\
要從儲存空間解除配置之第一個物件的指標。

*計數*\
要從儲存空間解除配置的物件數目。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
