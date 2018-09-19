---
title: _bstr_t::Attach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eddbc7a01be66430759bb84c3ce6d840f37d098
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111208"
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