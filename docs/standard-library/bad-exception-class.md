---
title: bad_exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 94d1104b66fc6bd84e209caa23ce309cffd9fa85
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377814"
---
# <a name="badexception-class"></a>bad_exception 類別

此類別描述可以從非預期處理常式擲回的例外狀況。

## <a name="syntax"></a>語法

```cpp
class bad_exception    : public exception {};
```

## <a name="remarks"></a>備註

如果 `bad_exception` 包含在函式的擲回清單中，則 [unexpected](../standard-library/exception-functions.md#unexpected) 會擲回 `bad_exception`，而不是終止或呼叫使用 [set_unexpected](../standard-library/exception-functions.md#set_unexpected) 所指定的另一個函式。

所傳回的值`what`是一個實作定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。

如需 `bad_exception` 類別所繼承的成員清單，請參閱 [exception 類別](../standard-library/exception-class.md)。

## <a name="example"></a>範例

如需擲回 `bad_exception` 的 [unexpected](../standard-library/exception-functions.md#unexpected) 用法範例，請參閱 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)。

## <a name="requirements"></a>需求

**標頭：**\<exception>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[exception 類別](../standard-library/exception-class.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
