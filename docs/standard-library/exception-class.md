---
title: exception 類別
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: 5bef8190889ae00298760ea395fb524f557c2be2
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446825"
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

**Int**參數可讓您指定不應配置任何記憶體。 已忽略**int**的值。

> [!NOTE]
> 建構函式 `exception(const char* const &message)` 和 `exception(const char* const &message, int)` 是 Microsoft 的 C++ 標準程式庫延伸模組。

## <a name="example"></a>範例

如需繼承自 `exception` 類別之標準例外狀況類別的用法範例，請參閱 [\<stdexcept>](../standard-library/stdexcept.md) 中定義的任何類別。
