---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: a517c40e9adfbda2d790ce41a48ccf8658bcd3e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544387"
---
# <a name="comerrordescription"></a>_com_error::Description

**Microsoft 專屬**

呼叫`IErrorInfo::GetDescription`函式。

## <a name="syntax"></a>語法

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>傳回值

傳回的結果`IErrorInfo::GetDescription`for`IErrorInfo`物件記錄`_com_error`物件。 產生的 `BSTR` 會封裝在 `_bstr_t` 物件內。 如果沒有`IErrorInfo`是記錄，它會傳回空`_bstr_t`。

## <a name="remarks"></a>備註

呼叫`IErrorInfo::GetDescription`函式並擷取`IErrorInfo`記錄`_com_error`物件。 呼叫時的任何失敗`IErrorInfo::GetDescription`方法會被忽略。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)