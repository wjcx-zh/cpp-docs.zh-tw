---
title: nested_exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: a568a8d9a3817883656406d63c3dd948539bb385
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268520"
---
# <a name="nestedexception-class"></a>nested_exception 類別

此類別描述使用具有多重繼承的例外狀況。 它會擷取目前處理的例外狀況，並將其儲存供稍後使用。

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
|[rethrow_nested](#rethrow_nested)|預存的例外狀況會擲回。|
|[nested_ptr](#nested_ptr)|傳回預存的例外狀況。|

### <a name="op_as"></a> 運算子 =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a> nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>傳回值

擷取由這個預存的例外狀況`nested_exception`物件。

### <a name="rethrow_nested"></a> rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>備註

如果`nested_ptr()`會傳回 null 指標，函式呼叫`std::terminate()`。 否則，會擷取預存的例外狀況擲回`*this`。

## <a name="requirements"></a>需求

**標頭：** \<exception>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
