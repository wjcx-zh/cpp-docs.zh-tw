---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 8e2c52d10b15822703329dcea18944773f5784ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180754"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Microsoft 專屬**

抓取傳遞至此函數的 HRESULT。

## <a name="syntax"></a>語法

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>傳回值

傳遞至此函式的原始 HRESULT 專案。

## <a name="remarks"></a>備註

抓取 `_com_error` 物件中封裝的 HRESULT 專案。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)
