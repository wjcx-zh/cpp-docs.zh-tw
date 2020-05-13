---
title: '&lt;allocators&gt; 巨集'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: a8b988511d0cdd46ae7f41bce29eb26f593a57c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364976"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt; 巨集

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a><a name="allocator_decl"></a>ALLOCATOR_DECL

生成分配器類範本。

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>備註

`template <class Type> class name {.....}`巨集產生樣本定義和一個`template <> class name<void> {.....}`專門化,它們共同定義一個分配器類範本,`sync`該範本使用同步篩選器`cache`和類型的緩存。

針對可以編譯重新繫結的編譯器，產生的範本定義看起來如下︰

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

針對無法編譯重新繫結的編譯器，產生的範本定義看起來如下︰

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a><a name="cache_chunklist"></a>CACHE_CHUNKLIST

產生 `stdext::allocators::cache_chunklist<sizeof(Type)>`。

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>備註

## <a name="cache_freelist"></a><a name="cache_freelist"></a>CACHE_FREELIST

產生 `stdext::allocators::cache_freelist<sizeof(Type), max>`。

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>備註

## <a name="cache_suballoc"></a><a name="cache_suballoc"></a>CACHE_SUBALLOC

產生 `stdext::allocators::cache_suballoc<sizeof(Type)>`。

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>備註

## <a name="sync_default"></a><a name="sync_default"></a>SYNC_DEFAULT

產生同步處理篩選。

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>備註

如果編譯器支援編譯單一執行緒和多執行緒應用程式，則針對單一執行緒應用程式，巨集會產生 `stdext::allocators::sync_none`；在所有其他情況下，則會產生 `stdext::allocators::sync_shared`。

## <a name="see-also"></a>另請參閱

[\<配置器>](../standard-library/allocators-header.md)
