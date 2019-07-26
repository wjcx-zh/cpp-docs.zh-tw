---
title: nested_exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 5741b3aa255f915500f5fe79ab5374c8c86f8814
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460183"
---
# <a name="nestedexception-class"></a>nested_exception 類別

類別描述搭配多重繼承使用的例外狀況。 它會捕獲目前處理的例外狀況, 並加以儲存以供稍後使用。

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

### <a name="operators"></a>運算子

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>函式

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

這個`nested_exception`物件所捕捉到的儲存例外狀況。

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>備註

如果`nested_ptr()`傳回 null 指標, 則函式會`std::terminate()`呼叫。 否則, 它會擲回所捕捉`*this`到的儲存例外狀況。

## <a name="requirements"></a>需求

**標頭：** \<exception>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
