---
title: _bstr_t::copy |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50f9a17c93849dec49c2c9a72825a5797d8c040c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068620"
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