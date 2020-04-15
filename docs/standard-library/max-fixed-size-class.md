---
title: max_fixed_size 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 7f75dd71caa3cfcfec19264b1da62c6d47a3e01d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371011"
---
# <a name="max_fixed_size-class"></a>max_fixed_size 類別

描述 [max 類別](../standard-library/allocators-header.md)物件，此物件可將 [freelist](../standard-library/freelist-class.md) 物件的長度上限限制為固定值。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*麥克斯*|max 類別，可決定要在 `freelist` 中儲存的元素數目上限。|

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[max_fixed_size](#max_fixed_size)|建構類型 `max_fixed_size` 的物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[allocated](#allocated)|遞增已配置的記憶體區塊計數。|
|[交易](#deallocated)|遞減已配置的記憶體區塊計數。|
|[全](#full)|傳回指定是否應該為可用清單新增更多記憶體區塊的值。|
|[釋放](#released)|遞減可用清單上的記憶體區塊計數。|
|[saved](#saved)|遞增可用清單上的記憶體區塊計數。|

## <a name="requirements"></a>需求

**標頭︰** \<allocators>

**命名空間：** stdext

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a>max_fixed_size::已分配

遞增已配置的記憶體區塊計數。

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 此成員函數在每次成功調用`cache_freelist::allocate`運算符**new**後調用。 *參數_Nx*是運算符**new**分配區塊中的記憶體區塊數。

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a>max_fixed_size::d分配

遞減已配置的記憶體區塊計數。

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*_Nx*|遞增值。|

### <a name="remarks"></a>備註

此成員函式不會執行任何動作。 此成員函數在每次呼叫後呼叫`cache_freelist::deallocate`運算子**刪除**後呼叫 。 *參數_Nx*是由運算符**刪除**處理塊中的記憶體區塊數。

## <a name="max_fixed_sizefull"></a><a name="full"></a>max_fixed_size::完整

傳回指定是否應該為可用清單新增更多記憶體區塊的值。

```cpp
bool full();
```

### <a name="return-value"></a>傳回值

**如果為**`Max <= _Nblocks`true;否則,**假**。

### <a name="remarks"></a>備註

此成員函式會由 `cache_freelist::deallocate` 呼叫。 如果呼叫傳**回 true,** 則將記憶體區塊放在空閒清單中;如果呼叫`deallocate`回 true, 則將記憶體區塊放在可用清單中。如果返回 false,`deallocate`則呼叫運算符**刪除**以取消分配區塊。

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a>max_fixed_size:max_fixed_size

建構類型 `max_fixed_size` 的物件。

```cpp
max_fixed_size();
```

### <a name="remarks"></a>備註

此建構函式會將預存值 `_Nblocks` 初始化為零。

## <a name="max_fixed_sizereleased"></a><a name="released"></a>max_fixed_size::已發佈

遞減可用清單上的記憶體區塊計數。

```cpp
void released();
```

### <a name="remarks"></a>備註

遞減預存值 `_Nblocks`。 每當從空閒清單中刪除記憶體區,就會調用當前 max`released`[類](../standard-library/allocators-header.md)的成員函數。 `cache_freelist::allocate`

## <a name="max_fixed_sizesaved"></a><a name="saved"></a>max_fixed_size::已儲存

遞增可用清單上的記憶體區塊計數。

```cpp
void saved();
```

### <a name="remarks"></a>備註

此成員函式會遞增預存值 `_Nblocks`。 每當 `cache_freelist::deallocate` 將記憶體區塊放到可用清單上時，都會呼叫此成員函式。

## <a name="see-also"></a>另請參閱

[\<配置器>](../standard-library/allocators-header.md)
