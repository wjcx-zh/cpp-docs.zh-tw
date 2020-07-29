---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: b6029e98e83b171d9ab9f8f3f0282fa3f46ca167
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227591"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Microsoft 特定的**

建構已封裝 `BSTR` 的複本。

## <a name="syntax"></a>語法

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>參數

*fCopy*<br/>
如果為 **`true`** ，則**copy**會傳回包含的複本 `BSTR` ，否則**COPY**會傳回實際的 BSTR。

## <a name="remarks"></a>備註

傳回新配置已封裝 `BSTR` 物件的複本。

## <a name="example"></a>範例

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
