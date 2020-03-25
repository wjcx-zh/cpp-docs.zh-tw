---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: cedb9ccadc63166c43d980333d93a195254700d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180702"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft 專屬**

抓取傳遞至此函式的 `IErrorInfo` 物件。

## <a name="syntax"></a>語法

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳入建構函式的原始 `IErrorInfo` 項目。

## <a name="remarks"></a>備註

抓取 `_com_error` 物件中封裝的 `IErrorInfo` 專案，如果沒有記錄 `IErrorInfo` 專案，則為 Null。 呼叫端完成使用時，必須在傳回的物件上呼叫 `Release`。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
