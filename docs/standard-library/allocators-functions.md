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
ms.openlocfilehash: c2d9b84a2be42df38df36bb90c0b5aeee076bf6a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623616"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt; 巨集

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a><a name="allocator_decl"></a>ALLOCATOR_DECL

產生配置器類別範本。

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>備註

宏會產生範本定義 `template <class Type> class name {.....}` 和特製化， `template <> class name<void> {.....}` 以同時定義使用同步處理篩選準則和類型快取的配置器類別範本 `sync` `cache` 。

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

[\<allocators>](allocators-header.md)
