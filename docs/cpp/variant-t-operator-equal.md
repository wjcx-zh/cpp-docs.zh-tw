---
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 2db26a378526cd5f48992cb32ea46e9677125e66
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226954"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Microsoft 特定的**

## <a name="syntax"></a>語法

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>備註

將新值指派給 `_variant_t` 物件的運算子：

- **operator = （**  *varSrc*  **）** 將現有的指派 `VARIANT` 給 `_variant_t` 物件。

- **operator = （**  *pVarSrc*  **）** 將現有的指派 `VARIANT` 給 `_variant_t` 物件。

- **operator = （**  *var_t_Src*  **）** 將現有的 `_variant_t` 物件指派給 `_variant_t` 物件。

- **operator = （**  *sSrc*  **）** 將 **`short`** 整數值指派給 `_variant_t` 物件。

- **operator = （** `lSrc` **）** 會將 **`long`** 整數值指派給 `_variant_t` 物件。    

- **operator = （**  *fltSrc*  **）** 將 **`float`** 數值指派給 `_variant_t` 物件。

- **operator = （**  *dblSrc*  **）** 將 **`double`** 數值指派給 `_variant_t` 物件。

- **operator = （**  *cySrc*  **）** 將 `CY` 物件指派給 `_variant_t` 物件。

- **operator = （**  *bstrSrc*  **）** 將 `BSTR` 物件指派給 `_variant_t` 物件。

- **operator = （**  *wstrSrc*  **）** 將 Unicode 字串指派給 `_variant_t` 物件。

- **operator = （** `strSrc` **）** 會將多位元組字元串指派給 `_variant_t` 物件。    

- **operator = （** `bSrc` **）** 會將 **`bool`** 值指派給 `_variant_t` 物件。  

- **operator = （**  *pDispSrc*  **）** 將 `VT_DISPATCH` 物件指派給 `_variant_t` 物件。

- **operator = （**  *pIUnknownSrc*  **）** 將 `VT_UNKNOWN` 物件指派給 `_variant_t` 物件。

- **operator = （**  *decSrc*  **）** 將 `DECIMAL` 值指派給 `_variant_t` 物件。

- **operator = （** `bSrc` **）** 會將 `BYTE` 值指派給 `_variant_t` 物件。  

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
