---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: d89503e822d92bf6a1fcb2b6bb658d532af32c5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155042"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft 專屬**

對應到 16 位元的 32 位元 HRESULT `wCode`。

## <a name="syntax"></a>語法

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>參數

*hr*<br/>
對應到 16 位元的 32 位元 HRESULT `wCode`。

## <a name="return-value"></a>傳回值

16 位元`wCode`從 32 位元 HRESULT 對應。

## <a name="remarks"></a>備註

請參閱[_com_error:: wcode](../cpp/com-error-wcode.md)如需詳細資訊。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 類別](../cpp/com-error-class.md)