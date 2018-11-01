---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: 905b67577a65b81be0b4d18c7513652dd8c5f055
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661626"
---
# <a name="comerrorguid"></a>_com_error::GUID

**Microsoft 專屬**

呼叫`IErrorInfo::GetGUID`函式。

## <a name="syntax"></a>語法

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳回的結果`IErrorInfo::GetGUID`for`IErrorInfo`物件記錄`_com_error`物件。 如果沒有`IErrorInfo`記錄物件時，它會傳回`GUID_NULL`。

## <a name="remarks"></a>備註

呼叫時的任何失敗`IErrorInfo::GetGUID`方法會被忽略。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)