---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: cea3404e0732cb0e16b3fa9199ce95e3dfcc23f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618045"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR

**Microsoft 專屬**

指向由 `BSTR` 所包裝之 `_bstr_t` 的開頭。

## <a name="syntax"></a>語法

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>傳回值

由 `BSTR` 所包裝之 `_bstr_t` 的開頭。

## <a name="remarks"></a>備註

**GetBSTR**會影響所有`_bstr_t`物件共用`BSTR`。 多個`_bstr_t`態度`BSTR`透過複製建構函式使用並**運算子 =**。

## <a name="example"></a>範例

請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用範例**GetBSTR**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)