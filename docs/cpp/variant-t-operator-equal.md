---
title: "_variant_t::operator = | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t.operator="
  - "_variant_t::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 運算子, 使用特定 Visual C++ 物件"
  - "operator =, variant"
  - "operator=, variant"
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
## 語法  
  
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
  
## 備註  
 將新值指派給 `_variant_t` 物件的運算子：  
  
-   **operator\=\(**  *varSrc*  **\)**：將現有的 **VARIANT** 指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *pVarSrc*  **\)**：將現有的 **VARIANT** 指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *var\_t\_Src*  **\)**：將現有的 `_variant_t` 物件指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *sSrc*  **\)**：將 **short** 整數值指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  `lSrc`  **\)**：將 **long** 整數值指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *fltSrc*  **\)**：將 **float** 數值指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *dblSrc*  **\)**：將 **double** 數值指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *cySrc*  **\)**：將 **CY** 物件指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *bstrSrc*  **\)**：將 `BSTR` 物件指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *wstrSrc*  **\)**：將 Unicode 字串指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  `strSrc`  **\)**：將多位元組字串指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  `bSrc` **\)**：將 `bool` 值指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *pDispSrc*  **\)**：將 **VT\_DISPATCH** 物件指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *pIUnknownSrc*  **\)** ：將 **VT\_UNKNOWN** 物件指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  *decSrc*  **\)**：將 **DECIMAL** 值指派給 `_variant_t` 物件。  
  
-   **operator\=\(**  `bSrc` **\)**：將 **BYTE** 值指派給 `_variant_t` 物件。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_variant\_t 類別](../cpp/variant-t-class.md)