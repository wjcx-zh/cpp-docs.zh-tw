---
title: cache_chunklist 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f30cde375f05dbba30da58ad3e71aa5e9bac11c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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
|`Sz`|陣列中要配置的項目數。|

## <a name="remarks"></a>備註

此樣板類別使用 `operator new` 來配置原始記憶體的區塊 (Chunk)，並視需要對區塊 (Block) 進行子配置以為記憶體區塊 (Block) 配置儲存體；它會將已解除配置的記憶體區塊 (Block) 儲存在每個區塊 (Chunk) 的個別可用清單中，並在其記憶體區塊 (Block) 不再使用時，使用 `operator delete` 解除配置區塊 (Chunk)。

每個記憶體區塊 (Block) 會保留 `Sz` 個位元組的可用記憶體，以及其所屬區塊 (Chunk) 的指標。 每個區塊 (Chunk) 會保留 `Nelts` 個記憶體區塊 (Block)、三個指標、一個 int，以及 `operator new` 和 `operator delete` 所需的資料。

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
|`count`|所配置陣列中的元素數。|

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
|`ptr`|要從儲存體解除配置之第一個物件的指標。|
|`count`|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
