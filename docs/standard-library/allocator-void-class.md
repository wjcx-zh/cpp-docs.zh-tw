---
title: allocator&lt;void&gt; 類別
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: 5591570527946895d1e0456b23327d7fabc4bef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377916"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; 類別

範本類別配置器類型的特製化**void**，定義在此內容中有意義的型別。

## <a name="syntax"></a>語法

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>備註

此類別明確特製化樣板類別[allocator](../standard-library/allocator-class.md)型別的**void**。 其建構函式和指派運算子的行為與範本類別相同，但只會定義下列類型︰

- [const_pointer](../standard-library/allocator-class.md#const_pointer)。

- [pointer](../standard-library/allocator-class.md#pointer).

- [value_type](../standard-library/allocator-class.md#value_type)。

- [rebind](../standard-library/allocator-class.md#rebind)，一種巢狀範本類別。

## <a name="requirements"></a>需求

**標頭：**\<memory>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
