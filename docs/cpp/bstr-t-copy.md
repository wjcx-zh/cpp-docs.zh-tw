---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 13ddf57e0bdbdbcc0c5b487e879e14b000de3ad0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506831"
---
# <a name="bstrtcopy"></a>_bstr_t::copy

**Microsoft 專屬**

建構已封裝 `BSTR` 的複本。

## <a name="syntax"></a>語法

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>參數

*fCopy*<br/>
如果為 TRUE，**複製**會傳回一份內含`BSTR`，否則為**複製**傳回實際的 BSTR。

## <a name="remarks"></a>備註

傳回新配置已封裝 `BSTR` 物件的複本。

## <a name="example"></a>範例

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)