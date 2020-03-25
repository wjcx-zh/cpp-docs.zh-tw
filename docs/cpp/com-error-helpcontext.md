---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: b3c79bb069ef504680e83359d6ec90c803f16d9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180585"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Microsoft 專屬**

呼叫 `IErrorInfo::GetHelpContext` 函式。

## <a name="syntax"></a>語法

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳回 `_com_error` 物件中所記錄之 `IErrorInfo` 物件的 `IErrorInfo::GetHelpContext` 結果。 如果未記錄任何 `IErrorInfo` 物件，則會傳回零。

## <a name="remarks"></a>備註

呼叫 `IErrorInfo::GetHelpContext` 方法時的任何失敗都會被忽略。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
