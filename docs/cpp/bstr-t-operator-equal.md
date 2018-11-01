---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 97f0100d8a34253f3a1375d34b887d3d31a77f43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432574"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =

**Microsoft 專屬**

將新值指派給現有的 `_bstr_t` 物件。

## <a name="syntax"></a>語法

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>參數

*s1*<br/>
`_bstr_t` 物件，將被指派給現有的 `_bstr_t` 物件。

*s2*<br/>
多位元組字串，將被指派給現有的 `_bstr_t` 物件。

*s3*<br/>
Unicode 字串，將被指派給現有的 `_bstr_t` 物件。

*var*<br/>
`_variant_t` 物件，將被指派給現有的 `_bstr_t` 物件。

**結束 Microsoft 專屬**

## <a name="example"></a>範例

請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)如需使用的範例**運算子 =**。

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)