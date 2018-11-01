---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 606f553060e71ece18b3d48159ec40133be28965
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465464"
---
# <a name="comerrorerror"></a>_com_error::Error

**Microsoft 專屬**

擷取傳遞給建構函式的 HRESULT。

## <a name="syntax"></a>語法

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>傳回值

原始 HRESULT 的項目傳遞至建構函式。

## <a name="remarks"></a>備註

擷取封裝中的 HRESULT 項目`_com_error`物件。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error 類別](../cpp/com-error-class.md)