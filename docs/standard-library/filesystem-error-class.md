---
title: filesystem_error 類別
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 1d142057859f1ca173f8953b34c07bbb3803ecba
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835866"
---
# <a name="filesystem_error-class"></a>filesystem_error 類別

擲回所有例外狀況的基底類別，以報告低階系統溢位。

## <a name="syntax"></a>語法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>備註

類別可做為擲回之所有例外狀況的基類，以報告函數中的錯誤 \<filesystem> 。 它會儲存類型的物件，此物件會 `string` `mymesg` 在此呼叫，以供展示之用。 它也會儲存兩個類型的物件 `path` ，稱為 `mypval1` 和 `mypval2` 。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[filesystem_error](#filesystem_error)|結構 `filesystem_error` 訊息。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[path1](#path1)|傳回 `mypval1`。|
|[path2](#path2)|傳回 `mypval2`。|
|[哪些](#what)|傳回 `NTBS` 的指標。|

## <a name="requirements"></a>規格需求

**標頭：**\<filesystem>

**命名空間：** std::experimental::filesystem

## <a name="filesystem_error"></a><a name="filesystem_error"></a> filesystem_error

第一個函式會從 *what_arg* 和 *ec*來建立訊息。 第二個函式也會從其儲存所在的 *pval1*來建立訊息 `mypval1` 。 第三個函式也會從 *pval1*（其儲存所在的 `mypval1` *pval2*和從中儲存的）中，建立其訊息 `mypval2` 。

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

*電子商務*\
指定的錯誤碼。

*mypval1*\
進一步指定的訊息參數。

*mypval2*\
進一步指定的訊息參數。

## <a name="path1"></a><a name="path1"></a> path1

此成員函式會傳回 `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a><a name="path2"></a> path2

此成員函式會傳回 `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a><a name="what"></a> 哪些

成員函式會傳回的指標，該指標 `NTBS` 最好是由 `runtime_error::what()` 、 `system_error::what()` 、 `mymesg` 、和組成 `mypval1.native_string()` `mypval2.native_string()` 。

```cpp
const char *what() const noexcept;
```
