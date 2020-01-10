---
title: filesystem_error 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 7bd6b2d3d716ba25999388d44e7bd5a8d0750eb5
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127205"
---
# <a name="filesystem_error-class"></a>filesystem_error 類別

擲回所有例外狀況的基底類別，以報告低階系統溢位。

## <a name="syntax"></a>語法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>備註

此類別可作為擲回之所有例外狀況的基底類別，以在 \<filesystem> 中回報錯誤。 它會針對展示的目的`string`，儲存`mymesg`類型為的物件，在這裡稱為。 它也會儲存兩個類型`path`的物件`mypval1` ， `mypval2`稱為和。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[filesystem_error](#filesystem_error)|建立`filesystem_error`訊息。|

### <a name="functions"></a>函式

|||
|-|-|
|[path1](#path1)|傳回 `mypval1`。|
|[path2](#path2)|傳回 `mypval2`。|
|[what](#what)|傳回 `NTBS` 的指標。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="filesystem_error"></a>filesystem_error

第一個函式會從*what_arg*和*ec*來構造其訊息。 第二個函式也會從它儲存在中`mypval1`的 pval1，來建立它的訊息。 第三個函式也會從*pval1*（它儲存在`mypval1`中，以及從*pval2*儲存在中`mypval2`），來構造其訊息。

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>參數

*what_arg*\
指定的訊息。

*歐洲*\
指定的錯誤碼。

*mypval1*\
進一步指定的訊息參數。

*mypval2*\
進一步指定的訊息參數。

## <a name="path1"></a>path1

此成員函式會傳回 `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a>path2

此成員函式會傳回 `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a>我

此成員函式會傳回的指標`NTBS`，最好是`runtime_error::what()`由、 `system_error::what()`、 `mymesg`、 `mypval1.native_string()`和`mypval2.native_string()`所組成。

```cpp
const char *what() const noexcept;
```
