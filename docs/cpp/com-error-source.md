---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 43dd21297ddd54863d535402dddd59243d589eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180520"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Microsoft 專屬**

呼叫 `IErrorInfo::GetSource` 函式。

## <a name="syntax"></a>語法

```
_bstr_t Source() const;
```

## <a name="return-value"></a>傳回值

傳回 `_com_error` 物件中所記錄之 `IErrorInfo` 物件的 `IErrorInfo::GetSource` 結果。 產生的 `BSTR` 會封裝在 `_bstr_t` 物件內。 如果未記錄任何 `IErrorInfo`，則會傳回空的 `_bstr_t`。

## <a name="remarks"></a>備註

呼叫 `IErrorInfo::GetSource` 方法時的任何失敗都會被忽略。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
