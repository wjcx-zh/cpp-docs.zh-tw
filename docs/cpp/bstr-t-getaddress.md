---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: ca78bd1b607ba4a86bbc824887a7ec767cd5476e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181248"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Microsoft 專屬**

釋放任何現有字串並傳回新配置字串的位址。

## <a name="syntax"></a>語法

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>傳回值

由 `BSTR` 包裝的 `_bstr_t` 指標。

## <a name="remarks"></a>備註

**GetAddress**會影響共用 `BSTR`的所有 `_bstr_t` 物件。 有一個以上的 `_bstr_t` 可以透過使用複製的函式和**operator =** 來共用 `BSTR`。

## <a name="example"></a>範例

如需使用**GetAddress**的範例，請參閱[_Bstr_t：： Assign](../cpp/bstr-t-assign.md) 。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
