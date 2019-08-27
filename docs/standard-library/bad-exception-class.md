---
title: bad_exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 1795a44d2d31cfbad964b41ef03e4bf65b401352
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246199"
---
# <a name="badexception-class"></a>bad_exception 類別

此類別描述可以從非預期處理常式擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class bad_exception : public exception {};

bad_exception();
bad_exception(const bad_exception&);
bad_exception& operator=(const bad_exception&);
const char* what() const override;
```

## <a name="remarks"></a>備註

如果 `bad_exception` 包含在函式的擲回清單中，則 [unexpected](../standard-library/exception-functions.md#unexpected) 會擲回 `bad_exception`，而不是終止或呼叫使用 [set_unexpected](../standard-library/exception-functions.md#set_unexpected) 所指定的另一個函式。

所傳回的值`what`是一個實作定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。

如需 `bad_exception` 類別所繼承的成員清單，請參閱 [exception 類別](../standard-library/exception-class.md)。

## <a name="example"></a>範例

如需擲回 `bad_exception` 的 [unexpected](../standard-library/exception-functions.md#unexpected) 用法範例，請參閱 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。
