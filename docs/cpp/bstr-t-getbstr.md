---
title: _bstr_t::GetBSTR |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a62cd1c08409fb5915ebf42fa118c1e6124e29f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071857"
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