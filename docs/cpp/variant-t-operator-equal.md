---
title: "_variant_t::operator = |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t.operator=
- _variant_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator=, variant
- operator =, variant
- = operator, with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 850562235442ef8fed4f7b130948a5e92b15a1fb
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="varianttoperator-"></a>_variant_t::operator =
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
  
-   **運算子 = (***varSrc***)**指派現有**VARIANT**至`_variant_t`物件。      
  
-   **運算子 = (***pVarSrc***)**指派現有**VARIANT**至`_variant_t`物件。      
  
-   **運算子 = (***var_t_Src***)**指派現有`_variant_t`物件`_variant_t`物件。      
  
-   **運算子 = (***sSrc***)**指派**簡短**的整數值`_variant_t`物件。      
  
-   **運算子 = (**`lSrc`**)**指派**長**的整數值`_variant_t`物件。      
  
-   **運算子 = (***fltSrc***)**指派**float**數值`_variant_t`物件。      
  
-   **運算子 = (***dblSrc***)**指派**double**數值`_variant_t`物件。      
  
-   **運算子 = (***cySrc***)**指派**CY**物件`_variant_t`物件。      
  
-   **運算子 = (***bstrSrc***)**指派`BSTR`物件`_variant_t`物件。      
  
-   **運算子 = (***wstrSrc***)**會指派 Unicode 字串，將`_variant_t`物件。      
  
-   **運算子 = (**`strSrc`**)**指派的多位元組字串`_variant_t`物件。      
  
-   **運算子 = (** `bSrc` **)**指派`bool`值設定為`_variant_t`物件。    
  
-   **運算子 = (***pDispSrc***)**指派**VT_DISPATCH**物件`_variant_t`物件。      
  
-   **運算子 = (***pIUnknownSrc***)**指派**VT_UNKNOWN**物件`_variant_t`物件。      
  
-   **運算子 = (***decSrc***)**指派**十進位**值設定為`_variant_t`物件。      
  
-   **運算子 = (** `bSrc` **)**指派**位元組**值設定為`_variant_t`物件。    
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_variant_t 類別](../cpp/variant-t-class.md)
