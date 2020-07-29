---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 843d6aa0e04595143d7da585e95d58e97fe80db0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221831"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Microsoft 特定的**

建構 `_bstr_t` 物件。

## <a name="syntax"></a>語法

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>參數

*s1*<br/>
要複製的 `_bstr_t` 物件。

*s2*<br/>
多位元組字串。

*s3*<br/>
Unicode 字串

*var*<br/>
[_Variant_t](../cpp/variant-t-class.md)物件。

*bstr*<br/>
現有的 `BSTR` 物件。

*fCopy*<br/>
如果為 **`false`** ，則會將*bstr*引數附加至新的物件，而不需要藉由呼叫來建立複本 `SysAllocString` 。

## <a name="remarks"></a>備註

下表將說明 `_bstr_t`建構函式。

|建構函式|描述|
|-----------------|-----------------|
|`_bstr_t( )`|構造 `_bstr_t` 封裝 null 物件的預設物件 `BSTR` 。|
|`_bstr_t( _bstr_t&`  `s1`  `)`|將 `_bstr_t` 物件建構為另一個物件的複本。<br /><br /> 這是*淺層*複製，會遞增封裝物件的參考計數， `BSTR` 而不是建立新的。|
|`_bstr_t( char*`  `s2`  `)`|透過呼叫 `_bstr_t` 建構 `SysAllocString` 以建立新的 `BSTR` 物件並加以封裝。<br /><br /> 這個建構函式會先執行多位元組對 Unicode 的轉換。|
|`_bstr_t( wchar_t*`  `s3`  `)`|透過呼叫 `_bstr_t` 建構 `SysAllocString` 以建立新的 `BSTR` 物件並加以封裝。|
|`_bstr_t( _variant_t&`  `var`  `)`|先從封裝的 VARIANT 物件擷取 `_bstr_t` 物件，以從 `_variant_t` 物件建構 `BSTR` 物件。|
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|從現有的 `_bstr_t` 建構 `BSTR` 物件 (而非 `wchar_t*` 字串)。 如果*fCopy*為 false，則提供的 `BSTR` 會附加至新的物件，而不會使用建立新的複本 `SysAllocString` 。<br /><br /> 類型程式庫標題中的包裝函式會使用此建構函式封裝，並取得以介面方法傳回之 `BSTR` 的擁有權。|

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)<br/>
[_variant_t 類別](../cpp/variant-t-class.md)
