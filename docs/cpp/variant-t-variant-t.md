---
title: "_variant_t::_variant_t |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t::_variant_t
dev_langs: C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd85a54e9f73352894f6575051fe1ea8be0698fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t
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
 *varSrc*  
 A **VARIANT**物件複製到新`_variant_t`物件。  
  
 *pVarSrc*  
 指標**VARIANT**物件複製到新`_variant_t`物件。  
  
 *var_t_Src*  
 要複製到新的 `_variant_t` 物件中的 `_variant_t` 物件。  
  
 `fCopy`  
 如果為 false，提供**VARIANT**物件附加至新`_variant_t`物件，而不製作新複本所**VariantCopy**。  
  
 *ISrc sSrc*  
 要複製到新的 `_variant_t` 物件中的整數值。  
  
 `vtSrc`  
 **VARTYPE**新`_variant_t`物件。  
  
 *fltSrc dblSrc*  
 要複製到新的 `_variant_t` 物件中的數值。  
  
 `cySrc`  
 A **CY**物件複製到新`_variant_t`物件。  
  
 `bstrSrc`  
 要複製到新的 `_bstr_t` 物件中的 `_variant_t` 物件。  
  
 *strSrc wstrSrc*  
 要複製到新的 `_variant_t` 物件中的字串。  
  
 `bSrc`  
 要複製到新的 `bool` 物件中的 `_variant_t` 值。  
  
 `pIUknownSrc`  
 COM 介面指標**VT_UNKNOWN**物件封裝到新`_variant_t`物件。  
  
 `pDispSrc`  
 COM 介面指標**VT_DISPATCH**物件封裝到新`_variant_t`物件。  
  
 `decSrc`  
 A**十進位**值複製到新`_variant_t`物件。  
  
 `bSrc`  
 A**位元組**值複製到新`_variant_t`物件。  
  
 `cSrc`  
 要複製到新的 `char` 物件中的 `_variant_t` 值。  
  
 *usSrc*  
 A**不帶正負號短**值複製到新`_variant_t`物件。  
  
 *ulSrc*  
 要複製到新的 `unsigned long` 物件中的 `_variant_t` 值。  
  
 `iSrc`  
 要複製到新的 `int` 物件中的 `_variant_t` 值。  
  
 *uiSrc*  
 要複製到新的 `unsigned int` 物件中的 `_variant_t` 值。  
  
 *i8Src*  
 __**Int64**值複製到新`_variant_t`物件。  
  
 *ui8Src*  
 **不帶正負號的 __int64**值複製到新`_variant_t`物件。  
  
## <a name="remarks"></a>備註  
  
-   **_variant_t （)**建構空`_variant_t`物件`VT_EMPTY`。  
  
-   **_variant_t (VARIANT &***varSrc***)**建構`_variant_t`物件的複本**VARIANT**物件。 variant 類型會保留。  
  
-   **_variant_t (VARIANT\****pVarSrc***)**建構`_variant_t`物件的複本**VARIANT**物件。 variant 類型會保留。  
  
-   **_variant_t (_variant_t （& s)***var_t_Src***)**建構`_variant_t`從另一個物件`_variant_t`物件。 variant 類型會保留。  
  
-   **_variant_t (VARIANT &***varSrc* **，bool**`fCopy`**)**建構`_variant_t`從現有物件**VARIANT**物件。 如果`fCopy`是**false**、 **VARIANT**物件時，會附加至新的物件上，而不製作複本。  
  
-   **_variant_t (簡短***sSrc* **，VARTYPE**`vtSrc`**= VT_I2)**建構`_variant_t`型別的物件`VT_I2`或`VT_BOOL`從**簡短**整數值。 任何其他**VARTYPE**導致`E_INVALIDARG`錯誤。  
  
-   **_variant_t (長**`lSrc` **，VARTYPE**`vtSrc`**= VT_I4)**建構`_variant_t`型別的物件`VT_I4`， `VT_BOOL`，或`VT_ERROR`從**長**整數值。 任何其他**VARTYPE**導致`E_INVALIDARG`錯誤。  
  
-   **_variant_t (float**`fltSrc`**)**建構`_variant_t`型別的物件`VT_R4`從**float**數值。  
  
-   **_variant_t (double** `dblSrc` **，VARTYPE**`vtSrc`**= VT_R8)**建構`_variant_t`型別的物件`VT_R8`或`VT_DATE`從**double**數值。 任何其他**VARTYPE**導致`E_INVALIDARG`錯誤。  
  
-   **_variant_t (CY （& s)**`cySrc`**)**建構`_variant_t`型別的物件`VT_CY`從**CY**物件。  
  
-   **_variant_t (_bstr_t （& s)**`bstrSrc`**)**建構`_variant_t`型別的物件`VT_BSTR`從`_bstr_t`物件。 會配置新的 `BSTR`。  
  
-   **_variant_t (wchar_t \***  *wstrSrc***)**建構`_variant_t`型別的物件`VT_BSTR`從 Unicode 字串。 會配置新的 `BSTR`。  
  
-   **_variant_t (char\***`strSrc`**)**建構`_variant_t`型別的物件`VT_BSTR`從字串。 會配置新的 `BSTR`。  
  
-   **_variant_t (bool**`bSrc`**)**建構`_variant_t`型別的物件`VT_BOOL`從`bool`值。  
  
-   **_variant_t (IUnknown\***  `pIUknownSrc` **，bool**`fAddRef`**= true)**建構`_variant_t`型別的物件**VT_UNKNOWN**從 COM 介面指標。 如果`fAddRef`是**true**，然後`AddRef`要比對的呼叫所提供的介面指標上呼叫**發行**，會發生時`_variant_t`物件被終結。 您呼叫**發行**上提供的介面指標。 如果`fAddRef`是**false**，這個建構函式會提供的介面指標的擁有權; 請勿呼叫**發行**上提供的介面指標。  
  
-   **_variant_t (IDispatch\***  `pDispSrc` **，bool**`fAddRef`**= true)**建構`_variant_t`型別的物件**VT_DISPATCH**從 COM 介面指標。 如果`fAddRef`是**true**，然後`AddRef`要比對的呼叫所提供的介面指標上呼叫**發行**，會發生時`_variant_t`物件被終結。 您呼叫**發行**上提供的介面指標。 如果**fAddRef**是 false，這個建構函式會提供的介面指標的擁有權; 請勿呼叫**發行**上提供的介面指標。  
  
-   **_variant_t (十進位 （& s)**`decSrc`**)**建構`_variant_t`型別的物件**VT_DECIMAL**從**十進位**值。  
  
-   **_variant_t (位元組**`bSrc`**)**建構`_variant_t`型別的物件`VT_UI1`從**位元組**值。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)