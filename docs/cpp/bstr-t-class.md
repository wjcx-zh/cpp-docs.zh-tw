---
title: _bstr_t 類別
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: 3ef89c6f6742d528c427c49fd2a62d8820625e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190374"
---
# <a name="_bstr_t-class"></a>_bstr_t 類別

**Microsoft 專屬**

`_bstr_t` 物件會封裝[BSTR 資料類型](/previous-versions/windows/desktop/automat/bstr)。 類別會在適當時，透過函式呼叫來管理資源配置和解除配置，以 `SysAllocString` 及 `SysFreeString` 和其他 `BSTR` Api。 **_Bstr_t**類別會使用參考計數來避免過多的額外負荷。

### <a name="construction"></a>建築業

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|建構 `_bstr_t` 物件。|

### <a name="operations"></a>作業

|||
|-|-|
|[指派](../cpp/bstr-t-assign.md)|將 `BSTR` 複製到 `BSTR` 所包裝的 `_bstr_t` 中。|
|[附加](../cpp/bstr-t-attach.md)|將 `_bstr_t` 包裝函式連結至 `BSTR`。|
|[copy](../cpp/bstr-t-copy.md)|建構已封裝 `BSTR` 的複本。|
|[卸離](../cpp/bstr-t-detach.md)|傳回 `BSTR` 所包裝的 `_bstr_t`，並將 `BSTR` 與 `_bstr_t` 中斷連結。|
|[GetAddress](../cpp/bstr-t-getaddress.md)|指向 `BSTR` 所包裝的 `_bstr_t`。|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|指向由 `BSTR` 所包裝之 `_bstr_t` 的開頭。|
|[length](../cpp/bstr-t-length.md)|傳回 `_bstr_t` 中的字元數。|

### <a name="operators"></a>操作員

|||
|-|-|
|[operator =](../cpp/bstr-t-operator-equal.md)|將新值指派給現有的 `_bstr_t` 物件。|
|[運算子 + =](../cpp/bstr-t-operator-add-equal-plus.md)|將字元附加至 `_bstr_t` 物件的結尾。|
|[運算子 +](../cpp/bstr-t-operator-add-equal-plus.md)|串連兩個字串。|
|[運算子 !](../cpp/bstr-t-operator-logical-not.md)|檢查封裝的 `BSTR` 是否為 Null 字串。|
|[operator = =、！ =、\<、>、\<=、> =](../cpp/bstr-t-relational-operators.md)|比較兩個 `_bstr_t` 物件。|
|[運算子 wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|將指標擷取至封裝的 Unicode 或多位元組的 `BSTR` 物件。|

**END Microsoft 特定的**

## <a name="requirements"></a>需求

**標頭：** \<comutil.h. h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （請參閱[/zc： Wchar_t （Wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以取得詳細資訊）

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)
