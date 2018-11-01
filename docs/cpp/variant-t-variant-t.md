---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: b3575226199c15c4a9796fb439f65efb5a539225
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544101"
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t

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
指標`VARIANT`複製到新的物件`_variant_t`物件。

*var_t_Src*<br/>
要複製到新的 `_variant_t` 物件中的 `_variant_t` 物件。

*fCopy*<br/>
如果**假**，提供`VARIANT`物件附加至新`_variant_t`物件，而不製作新複本所`VariantCopy`。

*ISrc sSrc*<br/>
要複製到新的 `_variant_t` 物件中的整數值。

*vtSrc*<br/>
`VARTYPE`新`_variant_t`物件。

*fltSrc, dblSrc*<br/>
要複製到新的 `_variant_t` 物件中的數值。

*cySrc*<br/>
要複製到新的 `CY` 物件中的 `_variant_t` 物件。

*bstrSrc*<br/>
要複製到新的 `_bstr_t` 物件中的 `_variant_t` 物件。

*strSrc wstrSrc*<br/>
要複製到新的 `_variant_t` 物件中的字串。

*bSrc*<br/>
A **bool**複製到新的值`_variant_t`物件。

*pIUknownSrc*<br/>
VT_UNKNOWN 的物件，以封裝到新的 COM 介面指標`_variant_t`物件。

*pDispSrc*<br/>
VT_DISPATCH 的物件，以封裝到新的 COM 介面指標`_variant_t`物件。

*decSrc*<br/>
要複製到新的 `DECIMAL` 物件中的 `_variant_t` 值。

*bSrc*<br/>
要複製到新的 `BYTE` 物件中的 `_variant_t` 值。

*cSrc*<br/>
A **char**複製到新的值`_variant_t`物件。

*usSrc*<br/>
A **unsigned short**複製到新的值`_variant_t`物件。

*ulSrc*<br/>
A **unsigned long**複製到新的值`_variant_t`物件。

*iSrc*<br/>
**Int**複製到新的值`_variant_t`物件。

*uiSrc*<br/>
**不帶正負號的 int**複製到新的值`_variant_t`物件。

*i8Src*<br/>
**__Int64**複製到新的值`_variant_t`物件。

*ui8Src*<br/>
**Unsigned 的 __int64**複製到新的值`_variant_t`物件。

## <a name="remarks"></a>備註

- **_variant_t （)** 建構空`_variant_t`物件， `VT_EMPTY`。

- **_variant_t (VARIANT &***varSrc***)** 建構`_variant_t`物件從一份`VARIANT`物件。     variant 類型會保留。

- **_variant_t (VARIANT**<strong>\*</strong>*pVarSrc***)** 建構`_variant_t`物件從一份`VARIANT`物件。     variant 類型會保留。

- **_variant_t (_variant_t &***var_t_Src***)** 建構`_variant_t`物件從另一個`_variant_t`物件。     variant 類型會保留。

- **_variant_t (VARIANT &***varSrc* **，bool**`fCopy`**)** 建構`_variant_t`從現有的物件`VARIANT`物件。       如果*fCopy*是**false**，則**VARIANT**物件時，會附加至新的物件上，而不製作複本。

- **_variant_t (short***sSrc* **，VARTYPE**`vtSrc`**= VT_I2)** 建構`_variant_t`型別的物件 VT_I2 或 VT_BOOL 從**簡短**整數值。       任何其他`VARTYPE`E_INVALIDARG 錯誤所導致。

- **_variant_t (long** `lSrc` **，VARTYPE**`vtSrc`**= VT_I4)** 建構`_variant_t`物件類型為 VT_I4、 VT_BOOL 或從 VT_ERROR**長**整數值。       任何其他`VARTYPE`E_INVALIDARG 錯誤所導致。

- **_variant_t (float**`fltSrc`**)** 建構`_variant_t`物件的型別 VT_R4 來自**float**數值。    

- **_variant_t (double** `dblSrc` **，VARTYPE**`vtSrc`**= VT_R8)** 建構`_variant_t`物件的型別 VT_R8 或從 VT_DATE **雙精度浮點數**數值。       任何其他`VARTYPE`E_INVALIDARG 錯誤所導致。

- **_variant_t (CY &**`cySrc`**)** 建構`_variant_t`物件的類型從 VT_CY`CY`物件。    

- **_variant_t (_bstr_t &**`bstrSrc`**)** 建構`_variant_t`物件的類型從 VT_BSTR`_bstr_t`物件。     會配置新的 `BSTR`。

- **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc***)** 建構`_variant_t`從 Unicode 字串 VT_BSTR 類型的物件。   會配置新的 `BSTR`。

- **_variant_t (char**<strong>\*</strong>`strSrc`**)** 建構`_variant_t`VT_BSTR 類型從字串的物件。     會配置新的 `BSTR`。

- **_variant_t (bool**`bSrc`**)** 建構`_variant_t`物件的類型從 VT_BOOL **bool**值。    

- **_variant_t (IUnknown** <strong>\*</strong> `pIUknownSrc` **，bool**`fAddRef`**= true)** 建構`_variant_t`類型的物件VT_UNKNOWN 從 COM 介面指標。       如果`fAddRef`已 **，則為 true**，然後`AddRef`來比對呼叫提供的介面指標上呼叫`Release`，會發生時`_variant_t`物件被終結。 它可以決定是否要呼叫`Release`上提供的介面指標。 如果`fAddRef`是**假**，這個建構函式接受提供的介面指標的擁有權; 請勿呼叫`Release`上提供的介面指標。

- **_variant_t (IDispatch** <strong>\*</strong> `pDispSrc` **，bool**`fAddRef`**= true)** 建構`_variant_t`物件輸入 VT_DISPATCH 從 COM 介面指標。       如果`fAddRef`已 **，則為 true**，然後`AddRef`來比對呼叫提供的介面指標上呼叫`Release`，會發生時`_variant_t`物件被終結。 它可以決定是否要呼叫`Release`上提供的介面指標。 如果`fAddRef`是**假**，這個建構函式接受提供的介面指標的擁有權; 請勿呼叫`Release`上提供的介面指標。

- **_variant_t (十進位 &**`decSrc`**)** 建構`_variant_t`物件的類型從 VT_DECIMAL`DECIMAL`值。    

- **_variant_t (BYTE**`bSrc`**)** 建構`_variant_t`型別的物件`VT_UI1`從`BYTE`值。    

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)