---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 35a497c273f15c9755d3607e7907a3a48dad8dc8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180559"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft 專屬**

將 32-bit HRESULT 對應至16位 `wCode`。

## <a name="syntax"></a>語法

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>參數

*工時*<br/>
要對應至16位 `wCode`的32位 HRESULT。

## <a name="return-value"></a>傳回值

從32位 HRESULT 對應的16位 `wCode`。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱[_com_error：： WCode](../cpp/com-error-wcode.md) 。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 類別](../cpp/com-error-class.md)
