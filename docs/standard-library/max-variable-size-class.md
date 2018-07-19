---
title: max_variable_size 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 974cee757708b9f7b1e48ea3bec3c4af98ced558
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957644"
---
# <a name="maxvariablesize-class"></a>max_variable_size 類別

描述 [max 類別](../standard-library/allocators-header.md)物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為與已配置的記憶體區塊數目大致成正比。

## <a name="syntax"></a>語法

```cpp
class max_variable_size
```

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[max_variable_size](#max_variable_size)|建構類型 `max_variable_size` 的物件。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[allocated](#allocated)|遞增已配置的記憶體區塊計數。|
|[deallocated](#deallocated)|遞減已配置的記憶體區塊計數。|
|[full](#full)|傳回指定是否應該為可用清單新增更多記憶體區塊的值。|
|[released](#released)|遞減可用清單上的記憶體區塊計數。|
|[saved](#saved)|遞增可用清單上的記憶體區塊計數。|

## <a name="requirements"></a>需求

**標頭︰**\<allocators>

**命名空間：** stdext

## <a name="allocated"></a>  max_variable_size::allocated

遞增已配置的記憶體區塊計數。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

此成員函式會將 *_Nx*的預存值`_Nallocs`。 每個成功呼叫之後呼叫此成員函式`cache_freelist::allocate`運算子**新**。 引數 *_Nx*運算子所配置之區塊中的記憶體區塊數目**新**。

## <a name="deallocated"></a>  max_variable_size::deallocated

遞減已配置的記憶體區塊計數。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

此成員函式減去 *_Nx*預存值`_Nallocs`。 此成員函式會依每次呼叫之後呼叫`cache_freelist::deallocate`運算子**刪除**。 引數 *_Nx*是由運算子解除配置之區塊中的記憶體區塊數目**刪除**。

## <a name="full"></a>  max_variable_size::full

傳回指定是否應該為可用清單新增更多記憶體區塊的值。

```cpp
bool full();
```

### <a name="return-value"></a>傳回值

**真**如果`_Nallocs / 16 + 16 <= _Nblocks`。

### <a name="remarks"></a>備註

此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果呼叫傳回 **，則為 true**，`deallocate`如果傳回 false，記憶體區塊放到可用的清單;`deallocate`呼叫運算子**刪除**解除配置的區塊。

## <a name="max_variable_size"></a>  max_variable_size::max_variable_size

建構類型 `max_variable_size` 的物件。

```cpp
max_variable_size();
```

### <a name="remarks"></a>備註

此建構函式會將預存值 `_Nblocks` 和 `_Nallocs` 初始化為零。

## <a name="released"></a>  max_variable_size::released

遞減可用清單上的記憶體區塊計數。

```cpp
void released();
```

### <a name="remarks"></a>備註

此成員函式會遞減預存值 `_Nblocks`。 每當 `cache_freelist::allocate` 從可用清單中移除記憶體區塊時，都會呼叫目前 max 類別的 `released` 成員函式。

## <a name="saved"></a>  max_variable_size::saved

遞增可用清單上的記憶體區塊計數。

```cpp
void saved();
```

### <a name="remarks"></a>備註

此成員函式會遞增預存值 `_Nblocks`。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫此成員函式。

## <a name="see-also"></a>另請參閱

[\<allocators>](../standard-library/allocators-header.md)<br/>
