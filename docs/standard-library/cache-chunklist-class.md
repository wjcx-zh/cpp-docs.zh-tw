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
ms.openlocfilehash: 94ae4dfc8f5f9073c0a39f315adfbed3e5c14daf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380166"
---
# <a name="cachechunklist-class"></a>cache_chunklist 類別

定義[區塊配置器](../standard-library/allocators-header.md)以配置及解除配置單一大小的記憶體區塊。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*Sz*|所配置陣列中的元素數。|

## <a name="remarks"></a>備註

使用此範本類別**new 運算子**配置的未經處理的記憶體區塊，suballocating 封鎖來配置記憶體區塊時所需的儲存體，它會解除配置的記憶體區塊儲存在每個區塊，個別可用清單，並使用**運算子 delete**解除配置區塊，其記憶體區塊中沒有任何使用中時。

每個記憶體區塊會保留*Sz*個位元組的可用記憶體，以及其所屬區塊的指標。 每個區塊會保留`Nelts`記憶體區塊、 三個指標、 整數和資料所**new 運算子**並**運算子 delete**需要。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_chunklist](#cache_chunklist)|建構類型 `cache_chunklist` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

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

## <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist

建構類型 `cache_chunklist` 的物件。

```cpp
cache_chunklist();
```

### <a name="remarks"></a>備註

## <a name="deallocate"></a>  cache_chunklist::deallocate

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
