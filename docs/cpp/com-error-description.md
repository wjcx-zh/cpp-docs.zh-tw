---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: de2275f096fe2fde96e64cbc3034602a1fde5e88
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180767"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Microsoft 專屬**

呼叫 `IErrorInfo::GetDescription` 函式。

## <a name="syntax"></a>語法

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>傳回值

傳回 `_com_error` 物件中所記錄之 `IErrorInfo` 物件的 `IErrorInfo::GetDescription` 結果。 產生的 `BSTR` 會封裝在 `_bstr_t` 物件內。 如果未記錄任何 `IErrorInfo`，則會傳回空的 `_bstr_t`。

## <a name="remarks"></a>備註

呼叫 `IErrorInfo::GetDescription` 函式，並抓取 `_com_error` 物件內記錄的 `IErrorInfo`。 呼叫 `IErrorInfo::GetDescription` 方法時的任何失敗都會被忽略。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
