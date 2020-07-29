---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: 50c10eb4ff617f4bcdc69d2e1781a9920b9eb0e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233557"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Microsoft 特定的**

建構 `_variant_t` 物件。

## <a name="syntax"></a>語法

```
_variant_t( ) throw( );

_variant_t(
   const VARIANT& varSrc
);

_variant_t(
   const VARIANT* pVarSrc
);

_variant_t(
   const _variant_t& var_t_Src
);

_variant_t(
   VARIANT& varSrc,
   bool fCopy
);

_variant_t(
   short sSrc,
   VARTYPE vtSrc = VT_I2
);

_variant_t(
   long lSrc,
   VARTYPE vtSrc = VT_I4
);

_variant_t(
   float fltSrc
) throw( );

_variant_t(
   double dblSrc,
   VARTYPE vtSrc = VT_R8
);

_variant_t(
   const CY& cySrc
) throw( );

_variant_t(
   const _bstr_t& bstrSrc
);

_variant_t(
   const wchar_t *wstrSrc
);

_variant_t(
   const char* strSrc
);

_variant_t(
   IDispatch* pDispSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   bool bSrc
) throw( );

_variant_t(
   IUnknown* pIUknownSrc,
   bool fAddRef = true
) throw( );

_variant_t(
   const DECIMAL& decSrc
) throw( );

_variant_t(
   BYTE bSrc
) throw( );

variant_t(
   char cSrc
) throw();

_variant_t(
   unsigned short usSrc
) throw();

_variant_t(
   unsigned long ulSrc
) throw();

_variant_t(
   int iSrc
) throw();

_variant_t(
   unsigned int uiSrc
) throw();

_variant_t(
   __int64 i8Src
) throw();

_variant_t(
   unsigned __int64 ui8Src
) throw();
```

#### <a name="parameters"></a>參數

*varSrc*<br/>
要複製到新的 `VARIANT` 物件中的 `_variant_t` 物件。

*pVarSrc*<br/>
要複製到 `VARIANT` 新物件中之物件的指標 `_variant_t` 。

*var_t_Src*<br/>
要複製到新的 `_variant_t` 物件中的 `_variant_t` 物件。

*fCopy*<br/>
如果為 **`false`** ，則提供的 `VARIANT` 物件會附加至新的 `_variant_t` 物件，而不會建立新的複本 `VariantCopy` 。

*ISrc, sSrc*<br/>
要複製到新的 `_variant_t` 物件中的整數值。

*vtSrc*<br/>
`VARTYPE`新 `_variant_t` 物件的。

*fltSrc, dblSrc*<br/>
要複製到新的 `_variant_t` 物件中的數值。

*cySrc*<br/>
要複製到新的 `CY` 物件中的 `_variant_t` 物件。

*bstrSrc*<br/>
要複製到新的 `_bstr_t` 物件中的 `_variant_t` 物件。

*strSrc, wstrSrc*<br/>
要複製到新的 `_variant_t` 物件中的字串。

*bSrc*<br/>
**`bool`** 要複製到新物件中的值 `_variant_t` 。

*pIUknownSrc*<br/>
要封裝至新物件之 VT_UNKNOWN 物件的 COM 介面指標 `_variant_t` 。

*pDispSrc*<br/>
要封裝至新物件之 VT_DISPATCH 物件的 COM 介面指標 `_variant_t` 。

*decSrc*<br/>
要複製到新的 `DECIMAL` 物件中的 `_variant_t` 值。

*bSrc*<br/>
要複製到新的 `BYTE` 物件中的 `_variant_t` 值。

*cSrc*<br/>
**`char`** 要複製到新物件中的值 `_variant_t` 。

*usSrc*<br/>
**`unsigned short`** 要複製到新物件中的值 `_variant_t` 。

*ulSrc*<br/>
**`unsigned long`** 要複製到新物件中的值 `_variant_t` 。

*iSrc*<br/>
**`int`** 要複製到新物件中的值 `_variant_t` 。

*uiSrc*<br/>
**`unsigned int`** 要複製到新物件中的值 `_variant_t` 。

*i8Src*<br/>
**`__int64`** 要複製到新物件中的值 `_variant_t` 。

*ui8Src*<br/>
要複製到新物件中的不**帶正負號 __int64**值 `_variant_t` 。

## <a name="remarks"></a>備註

- **_variant_t （）** 建立空的 `_variant_t` 物件 `VT_EMPTY` 。

- **_variant_t （variant&** *varSrc***）**`_variant_t`從物件的複本來構造物件 `VARIANT` 。     variant 類型會保留。

- **_variant_t （variant** <strong>\*</strong> *pVarSrc***）** 會 `_variant_t` 從物件的複本來構造物件 `VARIANT` 。     variant 類型會保留。

- **_variant_t （_variant_t&** *var_t_Src***）**`_variant_t`從另一個物件來構造物件 `_variant_t` 。     variant 類型會保留。

- **_variant_t （variant&** *varSrc* **，bool** `fCopy` **）** 會 `_variant_t` 從現有的物件來構造物件 `VARIANT` 。       如果*fCopy*為 **`false`** ，則**VARIANT**物件會附加至新的物件，而不會建立複本。

- **_variant_t （short***sSrc* **，VARTYPE** `vtSrc` **= VT_I2）** 會 `_variant_t` 從整數值中，VT_I2 或 VT_BOOL 結構來建立類型的物件 **`short`** 。       任何其他會 `VARTYPE` 導致 E_INVALIDARG 錯誤。

- **_variant_t （long** `lSrc` **，VARTYPE** `vtSrc` **= VT_I4）** 會 `_variant_t` 從整數值中，VT_I4、VT_BOOL 或 VT_ERROR 結構來建立類型的物件 **`long`** 。       任何其他會 `VARTYPE` 導致 E_INVALIDARG 錯誤。

- **_variant_t （float** `fltSrc` **）** 會 `_variant_t` 從數值結構 VT_R4 類型的物件 **`float`** 。    

- **_variant_t （double** `dblSrc` **，VARTYPE** `vtSrc` **= VT_R8）** 會 `_variant_t` 從數值中，VT_R8 或 VT_DATE 來構造類型的物件 **`double`** 。       任何其他會 `VARTYPE` 導致 E_INVALIDARG 錯誤。

- **_variant_t （CY&** `cySrc` **）** 會 `_variant_t` 從物件中，建立類型 VT_CY 的物件 `CY` 。    

- **_variant_t （_bstr_t&** `bstrSrc` **）** 會 `_variant_t` 從物件中，建立 VT_BSTR 類型的物件 `_bstr_t` 。     會配置新的 `BSTR`。

- **_variant_t （wchar_t** <strong>\*</strong> *wstrSrc*  **）** 會 `_variant_t` 從 Unicode 字串中，VT_BSTR 類型的物件進行結構。 會配置新的 `BSTR`。

- **_variant_t （char** <strong>\*</strong> `strSrc`**）** 會 `_variant_t` 從字串中，VT_BSTR 類型的物件進行結構。     會配置新的 `BSTR`。

- **_variant_t （bool** `bSrc` **）** 會 `_variant_t` 從值中 VT_BOOL 類型的物件進行結構 **`bool`** 。    

- **_variant_t （IUnknown** <strong>\*</strong> `pIUknownSrc`**、bool** `fAddRef`**= true）**`_variant_t`從 COM 介面指標，建立 VT_UNKNOWN 類型的物件。       如果 `fAddRef` 為 **`true`** ，則 `AddRef` 會在提供的介面指標上呼叫，以符合 `Release` 將在物件終結時發生的呼叫 `_variant_t` 。 您必須 `Release` 在提供的介面指標上呼叫。 如果 `fAddRef` 為 **`false`** ，則此函式會取得所提供介面指標的擁有權; 不會 `Release` 在提供的介面指標上呼叫。

- **_variant_t （IDispatch）** <strong>\*</strong> `pDispSrc`**、bool** `fAddRef`**= true）**`_variant_t`從 COM 介面指標，建立 VT_DISPATCH 類型的物件。       如果 `fAddRef` 為 **`true`** ，則 `AddRef` 會在提供的介面指標上呼叫，以符合 `Release` 將在物件終結時發生的呼叫 `_variant_t` 。 您必須 `Release` 在提供的介面指標上呼叫。 如果 `fAddRef` 為 **`false`** ，則此函式會取得所提供介面指標的擁有權; 不會 `Release` 在提供的介面指標上呼叫。

- **_variant_t （DECIMAL&** `decSrc` **）** 會 `_variant_t` 從值 VT_DECIMAL 類型的物件 `DECIMAL` 。    

- **_variant_t （BYTE** `bSrc` **）** 會 `_variant_t` 從值來構造類型的物件 `VT_UI1` `BYTE` 。    

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
