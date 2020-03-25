---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: da438c65256d9a7e5bf5b02e108fee1385171d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181209"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Microsoft 專屬**

指向由 `BSTR` 所包裝之 `_bstr_t` 的開頭。

## <a name="syntax"></a>語法

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>傳回值

由 `BSTR` 所包裝之 `_bstr_t` 的開頭。

## <a name="remarks"></a>備註

**GetBSTR**會影響共用 `BSTR`的所有 `_bstr_t` 物件。 有一個以上的 `_bstr_t` 可以透過使用複製的函式和**operator =** 來共用 `BSTR`。

## <a name="example"></a>範例

如需使用**GetBSTR**的範例，請參閱[_Bstr_t：： Assign](../cpp/bstr-t-assign.md) 。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
