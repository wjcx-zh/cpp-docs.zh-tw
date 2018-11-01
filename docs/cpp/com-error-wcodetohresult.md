---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2fc84be53d95754d21c30eaea8dd981447453d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593051"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft 專屬**

將對應的 16 位元*wCode*成 32 位元 HRESULT。

## <a name="syntax"></a>語法

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>參數

*WCode*<br/>
16 位元*wCode*對應至 32 位元 HRESULT。

## <a name="return-value"></a>傳回值

從 16 位元對應的 32 位元 HRESULT *wCode*。

## <a name="remarks"></a>備註

請參閱[WCode](../cpp/com-error-wcode.md)成員函式。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error 類別](../cpp/com-error-class.md)