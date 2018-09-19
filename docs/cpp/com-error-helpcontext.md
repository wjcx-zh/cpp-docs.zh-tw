---
title: _com_error::HelpContext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c2a1810410194f1261da907199a3b6665e5be30
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074366"
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