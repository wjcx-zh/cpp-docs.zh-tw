---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 826ac53f001355127f16b7ad2a7583a0f8800de7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155029"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile

**Microsoft 專屬**

呼叫`IErrorInfo::GetHelpFile`函式。

## <a name="syntax"></a>語法

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>傳回值

傳回的結果`IErrorInfo::GetHelpFile`for`IErrorInfo`物件記錄`_com_error`物件。 產生的 BSTR 會封裝在 `_bstr_t` 物件內。 如果沒有`IErrorInfo`是記錄，它會傳回空`_bstr_t`。

## <a name="remarks"></a>備註

呼叫時的任何失敗`IErrorInfo::GetHelpFile`方法會被忽略。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)