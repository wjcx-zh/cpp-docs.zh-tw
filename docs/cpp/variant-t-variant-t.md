---
title: "_variant_t::_variant_t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t::_variant_t"
  - "_variant_t._variant_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_variant_t 類別, 建構函式"
  - "_variant_t 方法"
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# _variant_t::_variant_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 建構 `_variant_t` 物件。  
  
## 語法  
  
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
  
#### 參數  
 *varSrc*  
 要複製到新的 `_variant_t` 物件中的 **VARIANT** 物件。  
  
 *pVarSrc*  
 要複製到新的 `_variant_t` 物件中的 **VARIANT** 物件指標。  
  
 *var\_t\_Src*  
 要複製到新的 `_variant_t` 物件中的 `_variant_t` 物件。  
  
 `fCopy`  
 如果為 false，則提供的 **VARIANT** 物件會附加至新的 `_variant_t` 物件，而不使用 **VariantCopy** 製作新複本。  
  
 *ISrc, sSrc*  
 要複製到新的 `_variant_t` 物件中的整數值。  
  
 `vtSrc`  
 新 `_variant_t` 物件的 **VARTYPE**。  
  
 *fltSrc, dblSrc*  
 要複製到新的 `_variant_t` 物件中的數值。  
  
 `cySrc`  
 要複製到新的 `_variant_t` 物件中的 **CY** 物件。  
  
 `bstrSrc`  
 要複製到新的 `_variant_t` 物件中的 `_bstr_t` 物件。  
  
 *strSrc, wstrSrc*  
 要複製到新的 `_variant_t` 物件中的字串。  
  
 `bSrc`  
 要複製到新的 `_variant_t` 物件中的 `bool` 值。  
  
 `pIUknownSrc`  
 要封裝到新的 `_variant_t` 物件中之 **VT\_UNKNOWN** 物件的 COM 介面指標。  
  
 `pDispSrc`  
 要封裝到新的 `_variant_t` 物件中之 **VT\_DISPATCH** 物件的 COM 介面指標。  
  
 `decSrc`  
 要複製到新的 `_variant_t` 物件中的 **DECIMAL** 值。  
  
 `bSrc`  
 要複製到新的 `_variant_t` 物件中的 **BYTE** 值。  
  
 `cSrc`  
 要複製到新的 `_variant_t` 物件中的 `char` 值。  
  
 *usSrc*  
 要複製到新的 `_variant_t` 物件中的 **unsigned short** 值。  
  
 *ulSrc*  
 要複製到新的 `_variant_t` 物件中的 `unsigned long` 值。  
  
 `iSrc`  
 要複製到新的 `_variant_t` 物件中的 `int` 值。  
  
 *uiSrc*  
 要複製到新的 `_variant_t` 物件中的 `unsigned int` 值。  
  
 *i8Src*  
 要複製到新的 `_variant_t` 物件中的 \_\_**int64** 值。  
  
 *ui8Src*  
 要複製到新的 `_variant_t` 物件中的 **unsigned \_\_int64** 值。  
  
## 備註  
  
-   **\_variant\_t\( \)**：會建構空的 `_variant_t` 物件 `VT_EMPTY`。  
  
-   **\_variant\_t\( VARIANT&**  *varSrc*  **\)**：會從 **VARIANT** 物件的複本建構 `_variant_t` 物件。  variant 類型會保留。  
  
-   **\_variant\_t\( VARIANT\***  *pVarSrc*  **\)**：會從 **VARIANT** 物件的複本建構 `_variant_t` 物件。  variant 類型會保留。  
  
-   **\_variant\_t\( \_variant\_t&**  *var\_t\_Src*  **\)**：會從另一個 `_variant_t` 物件建構 `_variant_t` 物件。  variant 類型會保留。  
  
-   **\_variant\_t\( VARIANT&**  *varSrc* **, bool**  `fCopy`  **\)**：會從現有的 **VARIANT** 物件建構 `_variant_t` 物件。  如果 `fCopy` 是 **false**，則 **VARIANT** 物件會附加至新物件，而不製作複本。  
  
-   **\_variant\_t\( short**  *sSrc* **, VARTYPE**  `vtSrc`  **\= VT\_I2 \)**：會從 **short** 整數值建構 `VT_I2` 或 `VT_BOOL` 類型的 `_variant_t` 物件。  任何其他 **VARTYPE** 都會造成 `E_INVALIDARG` 錯誤。  
  
-   **\_variant\_t\( long**  `lSrc` **, VARTYPE**  `vtSrc`  **\= VT\_I4 \)**：會從 **long** 整數值建構 `VT_I4`、`VT_BOOL` 或 `VT_ERROR` 類型的 `_variant_t` 物件。  任何其他 **VARTYPE** 都會造成 `E_INVALIDARG` 錯誤。  
  
-   **\_variant\_t\( float**  `fltSrc`  **\)**：會從 **float** 數值建構 `VT_R4` 類型的 `_variant_t` 物件。  
  
-   **\_variant\_t\( double**  `dblSrc` **, VARTYPE**  `vtSrc`  **\= VT\_R8 \)**：會從 **double** 數值建構 `VT_R8` 或 `VT_DATE` 類型的 `_variant_t` 物件。  任何其他 **VARTYPE** 都會造成 `E_INVALIDARG` 錯誤。  
  
-   **\_variant\_t\( CY&**  `cySrc`  **\)**：會從 **CY** 物件建構 `VT_CY` 類型的 `_variant_t` 物件。  
  
-   **\_variant\_t\( \_bstr\_t&**  `bstrSrc`  **\)**：會從 `_bstr_t` 物件建構 `VT_BSTR` 類型的 `_variant_t` 物件。  會配置新的 `BSTR`。  
  
-   **\_variant\_t\( wchar\_t \*** *wstrSrc*  **\)**：會從 Unicode 字串建構 `VT_BSTR` 類型的 `_variant_t` 物件。  會配置新的 `BSTR`。  
  
-   **\_variant\_t\( char\***  `strSrc`  **\)**：會從字串建構 `VT_BSTR` 類型的 `_variant_t` 物件。  會配置新的 `BSTR`。  
  
-   **\_variant\_t\( bool**  `bSrc`  **\)**：會從 `bool` 值建構 `VT_BOOL` 類型的 `_variant_t` 物件。  
  
-   **\_variant\_t\( IUnknown\***  `pIUknownSrc` **, bool**  `fAddRef`  **\= true \)**：會從 COM 介面指標建構 **VT\_UNKNOWN** 類型的 `_variant_t` 物件。  如果 `fAddRef` 是 **true**，則會在提供的介面指標上呼叫 `AddRef`，以比對 `_variant_t` 物件終結時發生的 **Release** 呼叫。  您可以決定是否要在提供的介面指標上呼叫 **Release**。  如果 `fAddRef` 是 **false**，這個建構函式會取得所提供介面指標的擁有權。請不要在提供的介面指標上呼叫 **Release**。  
  
-   **\_variant\_t\( IDispatch\***  `pDispSrc` **, bool**  `fAddRef`  **\= true \)**：會從 COM 介面指標建構 **VT\_DISPATCH** 類型的 `_variant_t` 物件。  如果 `fAddRef` 是 **true**，則會在提供的介面指標上呼叫 `AddRef`，以比對 `_variant_t` 物件終結時發生的 **Release** 呼叫。  您可以決定是否要在提供的介面指標上呼叫 **Release**。  如果 **fAddRef** 是 false，這個建構函式會取得所提供介面指標的擁有權。請不要在提供的介面指標上呼叫 **Release**。  
  
-   **\_variant\_t\( DECIMAL&**  `decSrc`  **\)**：會從 **DECIMAL** 值建構 **VT\_DECIMAL** 類型的 `_variant_t` 物件。  
  
-   **\_variant\_t\( BYTE**  `bSrc`  **\)**：會從 **BYTE** 值建構 `VT_UI1` 類型的 `_variant_t` 物件。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_variant\_t 類別](../cpp/variant-t-class.md)