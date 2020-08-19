---
title: max_unbounded 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: e0254563cc60db4a171527735b373c2954a5a9e5
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561956"
---
# <a name="max_unbounded-class"></a>max_unbounded 類別

描述 [max 類別](../standard-library/allocators-header.md)物件，此物件不會限制 [freelist](../standard-library/freelist-class.md) 物件的長度上限。

## <a name="syntax"></a>語法

```cpp
class max_unbounded
```

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[allocated](#allocated)|遞增已配置的記憶體區塊計數。|
|[分配](#deallocated)|遞減已配置的記憶體區塊計數。|
|[full](#full)|傳回指定是否應該為可用清單新增更多記憶體區塊的值。|
|[釋放](#released)|遞減可用清單上的記憶體區塊計數。|
|[saved](#saved)|遞增可用清單上的記憶體區塊計數。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="max_unboundedallocated"></a><a name="allocated"></a> max_unbounded：：已配置

遞增已配置的記憶體區塊計數。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

*_Nx*\
遞增值。

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 每次成功呼叫運算子之後，都會呼叫它 `cache_freelist::allocate` **`new`** 。 引數 *_Nx* 是由運算子所配置之區塊中的記憶體區塊數目 **`new`** 。

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a> max_unbounded：:d eallocated

遞減已配置的記憶體區塊計數。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

*_Nx*\
遞增值。

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 每次呼叫運算子之後，都會呼叫此成員 `cache_freelist::deallocate` 函式 **`delete`** 。 引數 *_Nx* 是由運算子解除配置之區塊中的記憶體區塊數目 **`delete`** 。

## <a name="max_unboundedfull"></a><a name="full"></a> max_unbounded：： full

傳回指定是否應該為可用清單新增更多記憶體區塊的值。

```cpp
bool full();
```

### <a name="return-value"></a>傳回值

成員函式一律會傳回 **`false`** 。

### <a name="remarks"></a>備註

此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果呼叫傳回 **`true`** ，則 `deallocate` 會將記憶體區塊放在可用清單中; 如果傳回 false，則會 `deallocate` 呼叫運算子 **`delete`** 來解除配置區塊。

## <a name="max_unboundedreleased"></a><a name="released"></a> max_unbounded：：已發行

遞減可用清單上的記憶體區塊計數。

```cpp
void released();
```

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 max 類別的 `released` 成員函式。

## <a name="max_unboundedsaved"></a><a name="saved"></a> max_unbounded：：已儲存

遞增可用清單上的記憶體區塊計數。

```cpp
void saved();
```

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫它。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)
