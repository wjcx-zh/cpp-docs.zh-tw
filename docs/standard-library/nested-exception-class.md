---
title: nested_exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: ed58eb6cc074b54ae6801d2b11089af9a79f8c8f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441625"
---
# <a name="nested_exception-class"></a>nested_exception 類別

類別描述搭配多重繼承使用的例外狀況。 它會捕獲目前處理的例外狀況，並加以儲存以供稍後使用。

## <a name="syntax"></a>語法

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>成員

### <a name="operators"></a>操作員

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>Functions

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|擲回儲存的例外狀況。|
|[nested_ptr](#nested_ptr)|傳回預存的例外狀況。|

### <a name="op_as"></a>operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>傳回值

這個 `nested_exception` 物件所捕捉到的儲存例外狀況。

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>備註

如果 `nested_ptr()` 傳回 null 指標，則函數會呼叫 `std::terminate()`。 否則，它會擲回 `*this`所捕捉的儲存例外狀況。

## <a name="requirements"></a>需求

**標頭：** \<例外狀況 >

**命名空間:** std

## <a name="see-also"></a>另請參閱

[Exception 類別](../standard-library/exception-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
