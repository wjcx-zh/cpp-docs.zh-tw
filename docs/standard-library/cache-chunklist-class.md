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
ms.openlocfilehash: 73730e0a4a22e7f5e63809cc2c1603cbda1ab596
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449670"
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

此樣板類別會使用**new 運算子**來配置原始記憶體的區塊, suballocating 區塊則會在需要時配置記憶體區塊的儲存空間;它會將已解除配置的記憶體區塊儲存在每個區塊的個別可用清單中, 並在未使用任何記憶體區塊時, 使用**運算子 delete**來解除配置區塊。

每個記憶體區塊會保留可使用記憶體的*Sz*位元組和其所屬區塊的指標。 每個區塊`Nelts`都包含記憶體區塊、三個指標、一個 int 和**operator new**和**operator delete**所需的資料。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[cache_chunklist](#cache_chunklist)|建構類型 `cache_chunklist` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|說明|
|-|-|
|[allocate](#allocate)|配置記憶體區塊。|
|[deallocate](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

配置記憶體區塊。

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*計數*|所配置陣列中的元素數。|

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

|參數|說明|
|---------------|-----------------|
|*ptr*|要從儲存體解除配置之第一個物件的指標。|
|*計數*|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
