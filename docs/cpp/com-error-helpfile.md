---
title: _com_error::HelpFile |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f40ea4dd39e88508e6e12c9d7103b7a536902d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070545"
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