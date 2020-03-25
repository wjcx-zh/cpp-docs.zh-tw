---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 775adfa7d5dd5aca098edcd793c2164d65fe7efa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190218"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Microsoft 專屬**

呼叫 `IErrorInfo::GetHelpFile` 函式。

## <a name="syntax"></a>語法

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>傳回值

傳回 `_com_error` 物件中所記錄之 `IErrorInfo` 物件的 `IErrorInfo::GetHelpFile` 結果。 產生的 BSTR 會封裝在 `_bstr_t` 物件內。 如果未記錄任何 `IErrorInfo`，則會傳回空的 `_bstr_t`。

## <a name="remarks"></a>備註

呼叫 `IErrorInfo::GetHelpFile` 方法時的任何失敗都會被忽略。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
