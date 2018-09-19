---
title: _bstr_t 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04244357f7e372856aea28063ab0df9db6431e0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028684"
---
# <a name="bstrt-class"></a>_bstr_t 類別

**Microsoft 專屬**

A`_bstr_t`物件會封裝[BSTR 資料型別](/previous-versions/windows/desktop/automat/bstr)。 此類別管理資源配置和解除配置函式呼叫，以透過`SysAllocString`並`SysFreeString`和其他`BSTR`時適當的 Api。 **_Bstr_t**類別會使用參考計數避免過多的額外負荷。

### <a name="construction"></a>建構

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|建構 `_bstr_t` 物件。|

### <a name="operations"></a>作業

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|將 `BSTR` 複製到 `BSTR` 所包裝的 `_bstr_t` 中。|
|[Attach](../cpp/bstr-t-attach.md)|將 `_bstr_t` 包裝函式連結至 `BSTR`。|
|[copy](../cpp/bstr-t-copy.md)|建構已封裝 `BSTR` 的複本。|
|[Detach](../cpp/bstr-t-detach.md)|傳回 `BSTR` 所包裝的 `_bstr_t`，並將 `BSTR` 與 `_bstr_t` 中斷連結。|
|[GetAddress](../cpp/bstr-t-getaddress.md)|指向 `BSTR` 所包裝的 `_bstr_t`。|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|指向由 `BSTR` 所包裝之 `_bstr_t` 的開頭。|
|[length](../cpp/bstr-t-length.md)|傳回 `_bstr_t` 中的字元數。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](../cpp/bstr-t-operator-equal.md)|將新值指派給現有的 `_bstr_t` 物件。|
|[operator + =](../cpp/bstr-t-operator-add-equal-plus.md)|將字元附加至 `_bstr_t` 物件的結尾。|
|[運算子 +](../cpp/bstr-t-operator-add-equal-plus.md)|串連兩個字串。|
|[運算子 !](../cpp/bstr-t-operator-logical-not.md)|檢查封裝`BSTR`是 NULL 字串。|
|[運算子 = =、 ！ =、 \<，>， \<=、 > =](../cpp/bstr-t-relational-operators.md)|比較兩個 `_bstr_t` 物件。|
|[運算子 wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|將指標擷取至封裝的 Unicode 或多位元組的 `BSTR` 物件。|

**結束 Microsoft 專屬**

## <a name="requirements"></a>需求

**標頭：** \<comutil.h >

**Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱 < [/zc: wchar_t （wchar_t 是原生型別）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)