---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 8601ebbea6a9ab837c07518b018e83e8c0df226d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604434"
---
# <a name="bstrtattach"></a>_bstr_t::Attach

**Microsoft 專屬**

將 `_bstr_t` 包裝函式連結至 `BSTR`。

## <a name="syntax"></a>語法

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>參數

*s*<br/>
要與 `BSTR` 變數產生關聯或指派給該變數的 `_bstr_t`。

## <a name="remarks"></a>備註

如果 `_bstr_t` 先前已附加至另一個 `BSTR`，且其他 `_bstr_t` 變數都不會使用 `BSTR`，則 `_bstr_t` 將會清除 `BSTR` 資源。

## <a name="example"></a>範例

請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用範例**附加**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)