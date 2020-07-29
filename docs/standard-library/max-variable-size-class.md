---
title: max_variable_size 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: f98b5698ff14349abf9300799f00c6d9121bcf65
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222260"
---
# <a name="max_variable_size-class"></a>max_variable_size 類別

描述 [max 類別](../standard-library/allocators-header.md)物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為與已配置的記憶體區塊數目大致成正比。

## <a name="syntax"></a>語法

```cpp
class max_variable_size
```

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[max_variable_size](#max_variable_size)|建構類型 `max_variable_size` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[allocated](#allocated)|遞增已配置的記憶體區塊計數。|
|[解除配置](#deallocated)|遞減已配置的記憶體區塊計數。|
|[full](#full)|傳回指定是否應該為可用清單新增更多記憶體區塊的值。|
|[達到](#released)|遞減可用清單上的記憶體區塊計數。|
|[saved](#saved)|遞增可用清單上的記憶體區塊計數。|

## <a name="requirements"></a>需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a>max_variable_size：：已配置

遞增已配置的記憶體區塊計數。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

此成員函式會將 *_Nx*新增至預存值 `_Nallocs` 。 每次成功呼叫運算子之後，都會呼叫此成員函式 `cache_freelist::allocate` **`new`** 。 *_Nx*引數是運算子所配置之區塊中的記憶體區塊數目 **`new`** 。

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a>max_variable_size：:d eallocated

遞減已配置的記憶體區塊計數。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

成員函式會從預存值減去 *_Nx* `_Nallocs` 。 每次呼叫運算子之後，都會呼叫此成員 `cache_freelist::deallocate` 函式 **`delete`** 。 引數 *_Nx*是由運算子解除配置之區塊中的記憶體區塊數目 **`delete`** 。

## <a name="max_variable_sizefull"></a><a name="full"></a>max_variable_size：： full

傳回指定是否應該為可用清單新增更多記憶體區塊的值。

```cpp
bool full();
```

### <a name="return-value"></a>傳回值

**`true`** 如果為 `_Nallocs / 16 + 16 <= _Nblocks` 。

### <a name="remarks"></a>備註

此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果呼叫傳回 **`true`** ，則 `deallocate` 會將記憶體區塊放在可用的清單上; 如果傳回 false，則會 `deallocate` 呼叫運算子 **`delete`** 來解除配置區塊。

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a>max_variable_size：： max_variable_size

建構類型 `max_variable_size` 的物件。

```cpp
max_variable_size();
```

### <a name="remarks"></a>備註

此建構函式會將預存值 `_Nblocks` 和 `_Nallocs` 初始化為零。

## <a name="max_variable_sizereleased"></a><a name="released"></a>max_variable_size：：已發行

遞減可用清單上的記憶體區塊計數。

```cpp
void released();
```

### <a name="remarks"></a>備註

此成員函式會遞減預存值 `_Nblocks`。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 max 類別的 `released` 成員函式。

## <a name="max_variable_sizesaved"></a><a name="saved"></a>max_variable_size：：已儲存

遞增可用清單上的記憶體區塊計數。

```cpp
void saved();
```

### <a name="remarks"></a>備註

此成員函式會遞增預存值 `_Nblocks`。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫此成員函式。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
