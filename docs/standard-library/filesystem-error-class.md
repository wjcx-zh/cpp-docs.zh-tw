---
title: filesystem_error 類別 | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
dev_langs:
- C++
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5756c01969dba0773e0327e1a34a0c7492b972a
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691519"
---
# <a name="filesystemerror-class"></a>filesystem_error 類別

擲回所有例外狀況的基底類別，以報告低階系統溢位。

## <a name="syntax"></a>語法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>備註

此類別可作為擲回之所有例外狀況的基底類別，以在 \<filesystem> 中回報錯誤。 它會儲存類型的物件`string`，稱為`mymesg`這裡有展銷的目的。 它也會儲存兩個物件的型別`path`，稱為`mypval1`和`mypval2`。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[filesystem_error](#filesystem_error)|建構`filesystem_error`訊息。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[路徑 1](#path1)|傳回 `mypval1`。|
|[路徑 2](#path2)|傳回 `mypval2`。|
|[項目](#what)|傳回 `NTBS` 的指標。|

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error:: filesystem_error

第一個建構函式會建構其訊息從*what_arg*並*ec*。 第二個建構函式也會建構其訊息從*pval1*，其儲存在`mypval1`。 第三個建構函式也會建構其訊息從*pval1*，其儲存在`mypval1`，以及從*pval2*，其儲存在`mypval2`。

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

*what_arg*<br/>
指定的訊息。

*ec*<br/>
指定的錯誤碼。

*mypval1*<br/>
進一步指定的訊息參數。

*mypval2*<br/>
進一步指定的訊息參數。

## <a name="path1"></a> filesystem_error::path1

此成員函式會傳回 `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> filesystem_error::path2

此成員函式會傳回 `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> filesystem_error::what

此成員函式傳回的指標`NTBS`中，最好是從組成`runtime_error::what()`， `system_error::what()`， `mymesg`， `mypval1.native_string()`，和`mypval2.native_string()`。

```cpp
const char *what() const noexcept;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error 類別](../standard-library/system-error-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
