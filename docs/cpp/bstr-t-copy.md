---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 1fe8cfb5b644b3c7c34cf3325a91ebdf23a04946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190322"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Microsoft 專屬**

建構已封裝 `BSTR` 的複本。

## <a name="syntax"></a>語法

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>參數

*fCopy*<br/>
若為 TRUE， **copy**會傳回包含 `BSTR`的複本，否則**copy**會傳回實際的 BSTR。

## <a name="remarks"></a>備註

傳回新配置已封裝 `BSTR` 物件的複本。

## <a name="example"></a>範例

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
