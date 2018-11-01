---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 682070877f269967405677d027b20707c8366f61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644427"
---
# <a name="comerrorsource"></a>_com_error::Source

**Microsoft 專屬**

呼叫`IErrorInfo::GetSource`函式。

## <a name="syntax"></a>語法

```
_bstr_t Source() const;
```

## <a name="return-value"></a>傳回值

傳回的結果`IErrorInfo::GetSource`for`IErrorInfo`物件記錄`_com_error`物件。 產生的 `BSTR` 會封裝在 `_bstr_t` 物件內。 如果沒有`IErrorInfo`是記錄，它會傳回空`_bstr_t`。

## <a name="remarks"></a>備註

呼叫時的任何失敗`IErrorInfo::GetSource`方法會被忽略。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)