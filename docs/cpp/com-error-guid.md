---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: d5b05cd4e26f89d42ea23b605f5e6560795a0cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180637"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Microsoft 專屬**

呼叫 `IErrorInfo::GetGUID` 函式。

## <a name="syntax"></a>語法

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳回 `_com_error` 物件中所記錄之 `IErrorInfo` 物件的 `IErrorInfo::GetGUID` 結果。 如果未記錄任何 `IErrorInfo` 物件，則會傳回 `GUID_NULL`。

## <a name="remarks"></a>備註

呼叫 `IErrorInfo::GetGUID` 方法時的任何失敗都會被忽略。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
