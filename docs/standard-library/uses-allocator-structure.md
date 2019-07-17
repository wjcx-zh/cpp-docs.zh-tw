---
title: uses_allocator 結構
ms.date: 11/04/2016
f1_keywords:
- future/std::uses_allocator
ms.assetid: c418f002-62e9-4806-b70c-41c663cae583
ms.openlocfilehash: 2cee318832caf70e781fa9e3490a752b097a5fbb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245679"
---
# <a name="usesallocator-structure"></a>uses_allocator 結構

永遠成立的特製化。

## <a name="syntax"></a>語法

```cpp
template <class Ty, class Alloc>
struct uses_allocator<promise<Ty>, Alloc> : true_type;
template <class Ty, class Alloc>
struct uses_allocator<packaged_task<Ty>, Alloc> : true_type;
```

## <a name="requirements"></a>需求

**標頭：** \<未來 >

**命名空間：** std

## <a name="specializations"></a>特製化

### <a name="tuple"></a> \<tuple >

```cpp
template <class... Types, class Alloc>
struct uses_allocator<tuple<Types...>, Alloc>;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
