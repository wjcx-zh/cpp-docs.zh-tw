---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 59ada8a7e098e57cca5641a439365851bbae2485
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155068"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft 專屬**

擷取`IErrorInfo`物件傳遞至建構函式。

## <a name="syntax"></a>語法

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳入建構函式的原始 `IErrorInfo` 項目。

## <a name="remarks"></a>備註

擷取封裝`IErrorInfo`中的項目`_com_error`物件，或如果沒有則為 NULL`IErrorInfo`項目記錄。 呼叫端必須呼叫`Release`上傳回的物件完成時使用它。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)