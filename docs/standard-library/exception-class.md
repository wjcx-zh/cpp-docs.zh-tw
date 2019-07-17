---
title: exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 90906469e923d29dd886930bd36944e4292bd9cd
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246074"
---
# <a name="exception-class"></a>exception 類別

此類別可作為特定運算式和 C++ 標準程式庫所擲回之所有例外狀況的基底類別。

## <a name="syntax"></a>語法

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
};
```

## <a name="remarks"></a>備註

具體來說，這個基底類別是 [\<stdexcept>](../standard-library/stdexcept.md) 中定義之標準例外狀況類別的根本。 預設建構函式不會指定 `what` 所傳回的 C 字串值，但特定衍生類別的建構函式可能會將其定義為由實作定義的 C 字串。 所有成員函式都不會擲回任何例外狀況。

**Int**參數可讓您指定應配置任何記憶體。 值**int**會被忽略。

> [!NOTE]
> 建構函式 `exception(const char* const &message)` 和 `exception(const char* const &message, int)` 是 Microsoft 的 C++ 標準程式庫延伸模組。

## <a name="example"></a>範例

如需繼承自 `exception` 類別之標準例外狀況類別的用法範例，請參閱 [\<stdexcept>](../standard-library/stdexcept.md) 中定義的任何類別。
