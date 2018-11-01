---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: a421a7fd7fa0817c74dac66946e28928b2ad82dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648700"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext

**Microsoft 專屬**

呼叫`IErrorInfo::GetHelpContext`函式。

## <a name="syntax"></a>語法

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳回的結果`IErrorInfo::GetHelpContext`for`IErrorInfo`物件記錄`_com_error`物件。 如果沒有`IErrorInfo`會記錄物件，它會傳回零。

## <a name="remarks"></a>備註

呼叫時的任何失敗`IErrorInfo::GetHelpContext`方法會被忽略。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)