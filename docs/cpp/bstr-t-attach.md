---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 718efb9e3dac0d776678fe9efd912a602e041659
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749697"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Microsoft 特定的**

將 `_bstr_t` 包裝函式連結至 `BSTR`。

## <a name="syntax"></a>語法

```cpp
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

有關使用**額外**的範例,請參閱[_bstr_t::分配](../cpp/bstr-t-assign.md)。

**結束微軟的**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
