---
title: nested_exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception/std::nested_exception
helpviewer_keywords:
- nested_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 4ab48f714e8b4de1a47674f1af8fe25467279f94
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836435"
---
# <a name="nested_exception-class"></a>nested_exception 類別

類別描述用於多重繼承的例外狀況。 它會捕獲目前處理的例外狀況，並加以儲存以供稍後使用。

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

|名稱|描述|
|-|-|
|[運算子 =](#op_as)|指派運算子。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[rethrow_nested](#rethrow_nested)|擲回儲存的例外狀況。|
|[nested_ptr](#nested_ptr)|傳回預存的例外狀況。|

### <a name="operator"></a><a name="op_as"></a> 運算子 =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a><a name="nested_ptr"></a> nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>傳回值

這個物件所捕捉的儲存例外狀況 `nested_exception` 。

### <a name="rethrow_nested"></a><a name="rethrow_nested"></a> rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>備註

如果傳回 `nested_ptr()` null 指標，則函式會呼叫 `std::terminate()` 。 否則，它會擲回所捕捉的儲存例外狀況 **`*this`** 。

## <a name="requirements"></a>規格需求

**標頭：**\<exception>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
