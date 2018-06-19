---
title: filesystem_error 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e1acf34f8478bc075b53780f1e48df125c22608b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845488"
---
# <a name="filesystemerror-class"></a>filesystem_error 類別

擲回所有例外狀況的基底類別，以報告低階系統溢位。

## <a name="syntax"></a>語法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>備註

此類別可作為擲回之所有例外狀況的基底類別，以在 \<filesystem> 中回報錯誤。 它會儲存 string 類型物件，這裡稱為 mymesg 主要是為了公開的目的。 它也會儲存兩個 path 類型物件，稱為 mypval1 和 mypval2。

## <a name="filesystemerrorfilesystemerror"></a>filesystem_error::filesystem_error

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

第一個建構函式會從 what_arg 和 ec 建構其訊息。 第二個建構函式也會從 pval1 建構其訊息，並存放在 mypval1。 第三個建構函式也會從 pval1 與 pval2 建構其訊息，並存放在 mypval1 和 mypval2 中。

## <a name="filesystemerrorpath1"></a>filesystem_error::path1

```cpp
const path& path1() const noexcept;
```

成員函式傳回 mypval1

## <a name="filesystemerrorpath2"></a>filesystem_error::path2

```cpp
const path& path2() const noexcept;
```

成員函式傳回 mypval2

## <a name="filesystemerrorwhat"></a>filesystem_error::what

```cpp
const char *what() const noexcept;
```

成員函式會傳回 NTBS 的指標，最好是由 runtime_error::what()、system_error::what()、mymesg、mypval1.native_string() 和 mypval2.native_string() 組成 。

## <a name="requirements"></a>需求

**標頭：** \<filesystem >

**命名空間：** std::experimental::filesystem

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error 類別](../standard-library/system-error-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
