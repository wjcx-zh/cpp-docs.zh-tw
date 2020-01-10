---
title: max_none 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: b296c641be68efac7410328a448a4ad2bd0fa88e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626822"
---
# <a name="max_none-class"></a>max_none 類別

描述 [max 類別](../standard-library/allocators-header.md)物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為零。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*最大值*|max 類別，可決定要在 `freelist` 中儲存的元素數目上限。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[allocated](#allocated)|遞增已配置的記憶體區塊計數。|
|[deallocated](#deallocated)|遞減已配置的記憶體區塊計數。|
|[full](#full)|傳回指定是否應該為可用清單新增更多記憶體區塊的值。|
|[released](#released)|遞減可用清單上的記憶體區塊計數。|
|[saved](#saved)|遞增可用清單上的記憶體區塊計數。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="allocated"></a>  max_none::allocated

遞增已配置的記憶體區塊計數。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 每次成功呼叫之後都會呼叫它，方法是 `cache_freelist::allocate` to operator **new**。 引數 *_Nx*是 operator **new**所配置之區塊中的記憶體區塊數目。

## <a name="deallocated"></a>  max_none::deallocated

遞減已配置的記憶體區塊計數。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 此成員函式會在每次呼叫之後，透過 `cache_freelist::deallocate` to operator **delete**來呼叫。 引數 *_Nx*是由 operator **delete**解除配置之區塊中的記憶體區塊數目。

## <a name="full"></a>  max_none::full

傳回指定是否應該為可用清單新增更多記憶體區塊的值。

```cpp
bool full();
```

### <a name="return-value"></a>傳回值

這個成員函式一律會傳回**true**。

### <a name="remarks"></a>備註

此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果呼叫傳回**true**，`deallocate` 會將記憶體區塊放在可用的清單上;如果傳回**false**，`deallocate` 會呼叫 operator **delete**來解除配置區塊。

## <a name="released"></a>  max_none::released

遞減可用清單上的記憶體區塊計數。

```cpp
void released();
```

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 max 類別的 `released` 成員函式。

## <a name="saved"></a>  max_none::saved

遞增可用清單上的記憶體區塊計數。

```cpp
void saved();
```

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫它。

## <a name="see-also"></a>請參閱

[\<allocators>](../standard-library/allocators-header.md)
