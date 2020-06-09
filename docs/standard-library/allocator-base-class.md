---
title: allocator_base 類別
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
ms.openlocfilehash: b55a7ec92787cb6b3103bf71b65d137d24ffff04
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617579"
---
# <a name="allocator_base-class"></a>allocator_base 類別

定義從同步處理篩選條件建立使用者定義的配置器時所需的基底類別和一般功能。

## <a name="syntax"></a>語法

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*型別*|配置器所配置的元素類型。|
|*同步處理*|配置器的同步處理原則，即 [sync_none 類別](sync-none-class.md)、[sync_per_container 類別](sync-per-container-class.md)、[sync_per_thread 類別](sync-per-thread-class.md)或 [sync_shared 類別](sync-shared-class.md)。|

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[allocator_base](#allocator_base)|建構類型 `allocator_base` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[const_pointer](#const_pointer)|一種類型，可提供配置器管理之物件類型的常數指標。|
|[const_reference](#const_reference)|一種類型，可提供配置器管理之物件類型的常數參考。|
|[difference_type](#difference_type)|帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。|
|[滑鼠](#pointer)|一種類型，可提供配置器管理之物件類型的指標。|
|[證明](#reference)|一種類型，可提供配置器管理之物件類型的參考。|
|[size_type](#size_type)|不帶正負號的整數類型，可以表示類型物件可以配置的任何序列的長度 `allocator_base` 。|
|[value_type](#value_type)|配置器所管理的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[_Charalloc](#charalloc)|為**char**類型的陣列配置儲存體。|
|[_Chardealloc](#chardealloc)|釋放包含**char**類型元素之陣列的儲存體。|
|[address](#address)|尋找指定值所屬物件的位址。|
|[allocate](#allocate)|配置夠大的記憶體區塊，至少儲存某些指定的項目數。|
|[建構](#construct)|在指定值初始化的指定位址上，建構特定類型的物件。|
|[解除配置](#deallocate)|從指定位置起算的儲存體中，釋放指定數目的物件。|
|[予以](#destroy)|呼叫物件解構函式，而不取消配置儲存物件的記憶體。|
|[max_size](#max_size)|傳回在可用記憶體用完之前，無法由 allocator 類別的物件所配置之類型 *Type* 的元素數。|

## <a name="requirements"></a>規格需求

**標頭：**\<allocators>

**命名空間：** stdext

## <a name="allocator_base_charalloc"></a><a name="charalloc"></a>allocator_base：： _Charalloc

為**char**類型的陣列配置儲存體。

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*計數*|所配置陣列中的元素數。|

### <a name="return-value"></a>傳回值

所配置物件的指標。

### <a name="remarks"></a>備註

使用無法編譯重新繫結的編譯器進行編譯時，容器會使用此成員函式。 它會實作使用者定義配置器的 `_Charalloc`，方法是傳回同步處理篩選之 `allocate` 函式呼叫的結果。

## <a name="allocator_base_chardealloc"></a><a name="chardealloc"></a>allocator_base：： _Chardealloc

釋放包含**char**類型元素之陣列的儲存體。

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*ptr*|要從儲存空間解除配置之第一個物件的指標。|
|*計數*|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

使用無法編譯重新繫結的編譯器進行編譯時，容器會使用此成員函式。 它會實作使用者定義配置器的 `_Chardealloc`，方法是呼叫同步處理篩選的 `deallocate` 函式。 之前必須已傳回指標 ptr，方法是呼叫等於 `*this` 之配置器物件的 `_Charalloc`，並配置相同大小和類型的陣列物件。 `_Chardealloc` 絕不會擲回例外狀況。

## <a name="allocator_baseaddress"></a><a name="address"></a>allocator_base：： address

尋找指定值所屬物件的位址。

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>參數

*初始值*\
搜尋其位址之物件的 const 或 nonconst 值。

### <a name="return-value"></a>傳回值

分別針對 const 或 nonconst 值找到之物件的 const 或 nonconst 指標。

### <a name="remarks"></a>備註

傳回 `&val`，即會針對使用者定義的配置器實作這個成員函式。

## <a name="allocator_baseallocate"></a><a name="allocate"></a>allocator_base：： allocate

配置夠大的記憶體區塊，至少儲存某些指定的項目數。

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*_Nx*|所配置陣列中的元素數。|
|*_Hint*|此參數會被忽略。|

### <a name="return-value"></a>傳回值

所配置物件的指標。

### <a name="remarks"></a>備註

如果 `_Nx == 1`，則成員函式會實作使用者定義配置器的記憶體配置，方法是傳回類型 Type `*` 之同步處理篩選的 `allocate` 函式呼叫的結果，否則方法是傳回 `operator new(_Nx * sizeof(Type))` 轉型為類型 Type `*` 之呼叫的結果。

## <a name="allocator_baseallocator_base"></a><a name="allocator_base"></a>allocator_base：： allocator_base

建構類型 `allocator_base` 的物件。

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*再*|要複製的配置器物件。|

### <a name="remarks"></a>備註

第一個建構函式會建構 [allocator_base](allocator-base-class.md) 執行個體。 第二個建構函式會建構 `allocator_base` 執行個體，因此適用於任何 `allocator_base<Type, _Sync>` 執行個體 `a`，`allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a`。

## <a name="allocator_baseconst_pointer"></a><a name="const_pointer"></a>allocator_base：： const_pointer

一種類型，可提供配置器管理之物件類型的常數指標。

```cpp
typedef const Type *const_pointer;
```

## <a name="allocator_baseconst_reference"></a><a name="const_reference"></a>allocator_base：： const_reference

一種類型，可提供配置器管理之物件類型的常數參考。

```cpp
typedef const Type& const_reference;
```

## <a name="allocator_baseconstruct"></a><a name="construct"></a>allocator_base：：結構

在指定值初始化的指定位址上，建構特定類型的物件。

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|要建構物件之位置的指標。|
|*初始值*|用來初始化所建構物件的值。|

### <a name="remarks"></a>備註

呼叫 `new((void*)ptr Type(val)`，即會針對使用者定義的配置器實作這個成員函式。

## <a name="allocator_basedeallocate"></a><a name="deallocate"></a>allocator_base：:d eallocate

從指定位置起算的儲存體中，釋放指定數目的物件。

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|要從儲存空間解除配置之第一個物件的指標。|
|*_Nx*|要從儲存空間解除配置的物件數目。|

### <a name="remarks"></a>備註

如果 `_Nx == 1`，則對同步處理篩選 `Sync` 呼叫 `deallocate(ptr)` 以針對使用者定義的配置器實作這個成員函式，否則是呼叫 `operator delete(_Nx * ptr)`。

## <a name="allocator_basedestroy"></a><a name="destroy"></a>allocator_base：:d estroy

呼叫物件解構函式，而不取消配置儲存物件的記憶體。

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ptr*|指定要終結之物件位址的指標。|

### <a name="remarks"></a>備註

呼叫 `ptr->~Type()`，即會針對使用者定義的配置器實作這個成員函式。

## <a name="allocator_basedifference_type"></a><a name="difference_type"></a>allocator_base：:d ifference_type

帶正負號整數類型，可以表示配置器所管理的物件類型的指標值之間的差異。

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="allocator_basemax_size"></a><a name="max_size"></a>allocator_base：： max_size

傳回在可用記憶體用完之前，無法由類別配置器的物件配置之類型 `Type` 的元素數。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>傳回值

無法配置的元素數。

### <a name="remarks"></a>備註

如果 `0 < (size_t)-1 / sizeof(Type)`，則會傳回 `(size_t)-1 / sizeof(Type)` 以針對使用者定義的配置器實作這個成員函式，否則為 `1`。

## <a name="allocator_basepointer"></a><a name="pointer"></a>allocator_base：:p ointer

一種類型，可提供配置器管理之物件類型的指標。

```cpp
typedef Type *pointer;
```

## <a name="allocator_basereference"></a><a name="reference"></a>allocator_base：： reference

一種類型，可提供配置器管理之物件類型的參考。

```cpp
typedef Type& reference;
```

## <a name="allocator_basesize_type"></a><a name="size_type"></a>allocator_base：： size_type

不帶正負號的整數類型，可以表示類型物件可以配置的任何序列的長度 `allocator_base` 。

```cpp
typedef std::size_t size_type;
```

## <a name="allocator_basevalue_type"></a><a name="value_type"></a>allocator_base：： value_type

配置器所管理的類型。

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>另請參閱

[\<allocators>](allocators-header.md)
