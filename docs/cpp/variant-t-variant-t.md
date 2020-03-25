---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: fff116ef04967a1887eaa075d92d3ea0283d5427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187527"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

**Microsoft 專屬**

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
要複製到新 `_variant_t` 物件之 `VARIANT` 物件的指標。

*var_t_Src*<br/>
要複製到新的 `_variant_t` 物件中的 `_variant_t` 物件。

*fCopy*<br/>
如果**為 false**，則提供的 `VARIANT` 物件會附加至新的 `_variant_t` 物件，而不會 `VariantCopy`建立新的複本。

*ISrc、sSrc*<br/>
要複製到新的 `_variant_t` 物件中的整數值。

*vtSrc*<br/>
新 `_variant_t` 物件的 `VARTYPE`。

*fltSrc, dblSrc*<br/>
要複製到新的 `_variant_t` 物件中的數值。

*cySrc*<br/>
要複製到新的 `CY` 物件中的 `_variant_t` 物件。

*bstrSrc*<br/>
要複製到新的 `_bstr_t` 物件中的 `_variant_t` 物件。

*strSrc, wstrSrc*<br/>
要複製到新的 `_variant_t` 物件中的字串。

*bSrc*<br/>
要複製到新的 `_variant_t` 物件中的**bool**值。

*pIUknownSrc*<br/>
要封裝到新 `_variant_t` 物件之 VT_UNKNOWN 物件的 COM 介面指標。

*pDispSrc*<br/>
要封裝到新 `_variant_t` 物件之 VT_DISPATCH 物件的 COM 介面指標。

*decSrc*<br/>
要複製到新的 `DECIMAL` 物件中的 `_variant_t` 值。

*bSrc*<br/>
要複製到新的 `BYTE` 物件中的 `_variant_t` 值。

*cSrc*<br/>
要複製到新的 `_variant_t` 物件中的**char**值。

*usSrc*<br/>
要複製到新的 `_variant_t` 物件中的不**帶正負**號的短值。

*ulSrc*<br/>
要複製到新的 `_variant_t` 物件中的不**帶正負**號的 long 值。

*iSrc*<br/>
要複製到新的 `_variant_t` 物件中的**int**值。

*uiSrc*<br/>
要複製到新的 `_variant_t` 物件中的不**帶正負號整數**值。

*i8Src*<br/>
要複製到新 `_variant_t` 物件中的 **__int64**值。

*ui8Src*<br/>
要複製到新 `_variant_t` 物件中的不**帶正負號 __int64**值。

## <a name="remarks"></a>備註

- **_variant_t （）** 建立空的 `_variant_t` 物件，`VT_EMPTY`。

- **_variant_t （variant &** *varSrc* **）** 從 `VARIANT` 物件的複本中，建立 `_variant_t` 物件。 variant 類型會保留。

- **_variant_t （variant** <strong>\*</strong> *pVarSrc* **）** 從 `VARIANT` 物件的複本中，建立 `_variant_t` 物件。 variant 類型會保留。

- **_variant_t （_variant_t &** *var_t_Src* **）** 從另一個 `_variant_t` 物件中，建立 `_variant_t` 物件。 variant 類型會保留。

- **_variant_t （variant &** *varSrc* **，bool**`fCopy` **）** 從現有的 `VARIANT` 物件中，建立 `_variant_t` 物件。 如果*fCopy*為**False**，則**VARIANT**物件會附加至新的物件，而不會建立複本。

- **_variant_t （short***sSrc* **，VARTYPE**`vtSrc` **= VT_I2）** 從**short**整數值中，VT_I2 或 VT_BOOL 類型的 `_variant_t` 物件。 任何其他 `VARTYPE` 都會導致 E_INVALIDARG 錯誤。

- **_variant_t （long**`lSrc` **，VARTYPE**`vtSrc` **= VT_I4）** 從**長**整數值中，建立 VT_I4、VT_BOOL 或 VT_ERROR 類型的 `_variant_t` 物件。 任何其他 `VARTYPE` 都會導致 E_INVALIDARG 錯誤。

- **_variant_t （float**`fltSrc` **）** 從**float**數值，建立 VT_R4 類型的 `_variant_t` 物件。

- **_variant_t （double**`dblSrc` **，VARTYPE**`vtSrc` **= VT_R8）** 從**double**數值中，VT_R8 或 VT_DATE 類型的 `_variant_t` 物件。 任何其他 `VARTYPE` 都會導致 E_INVALIDARG 錯誤。

- **_variant_t （CY &** `cySrc` **）** 從 `CY` 物件中，建立 VT_CY 類型的 `_variant_t` 物件。

- **_variant_t （_bstr_t &** `bstrSrc` **）** 從 `_bstr_t` 物件中，建立 VT_BSTR 類型的 `_variant_t` 物件。 會配置新的 `BSTR`。

- **_variant_t （wchar_t** <strong>\*</strong> *wstrSrc*  **）** 從 Unicode 字串中，建立 VT_BSTR 類型的 `_variant_t` 物件。 會配置新的 `BSTR`。

- **_variant_t （char** <strong>\*</strong>`strSrc` **）** 從字串中，建立 VT_BSTR 類型的 `_variant_t` 物件。 會配置新的 `BSTR`。

- **_variant_t （bool**`bSrc` **）** 從**BOOL**值，建立 VT_BOOL 類型的 `_variant_t` 物件。

- **_variant_t （IUnknown** <strong>\*</strong>`pIUknownSrc` **，bool**`fAddRef` **= true）** 從 COM 介面指標，建立 VT_UNKNOWN 類型的 `_variant_t` 物件。 如果 `fAddRef` 為**true**，則會在提供的介面指標上呼叫 `AddRef`，以符合 `_variant_t` 物件終結時將發生的 `Release` 呼叫。 您可以視需要在提供的介面指標上呼叫 `Release`。 如果 `fAddRef` 為**false**，則此函式會取得所提供介面指標的擁有權;請不要在提供的介面指標上呼叫 `Release`。

- **_variant_t （IDispatch** <strong>\*</strong>`pDispSrc` **，bool**`fAddRef` **= true）** 從 COM 介面指標，建立 VT_DISPATCH 類型的 `_variant_t` 物件。 如果 `fAddRef` 為**true**，則會在提供的介面指標上呼叫 `AddRef`，以符合 `_variant_t` 物件終結時將發生的 `Release` 呼叫。 您可以視需要在提供的介面指標上呼叫 `Release`。 如果 `fAddRef` 為**false**，則此函式會取得所提供介面指標的擁有權;請不要在提供的介面指標上呼叫 `Release`。

- **_variant_t （十進位 &** `decSrc` **）** 從 `DECIMAL` 值，建立 VT_DECIMAL 類型的 `_variant_t` 物件。

- **_variant_t （BYTE**`bSrc` **）** 從 `BYTE` 值，建立 `VT_UI1` 類型的 `_variant_t` 物件。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
