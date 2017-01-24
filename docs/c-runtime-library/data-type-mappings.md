---
title: "資料類型對應 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_TXCHAR"
  - "_TUCHAR"
  - "_TINT"
  - "_TSCHAR"
  - "_TCHAR"
  - "TCHAR::H"
  - "TCHAR"
  - "_T"
  - "_TEXT"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_T 類型"
  - "_TCHAR 類型"
  - "_TEXT 類型"
  - "_TINT 類型"
  - "_TSCHAR 類型"
  - "_TUCHAR 類型"
  - "_TXCHAR 類型"
  - "泛型文字資料類型"
  - "T 類型"
  - "TCHAR 類型"
  - "TCHAR.H 資料類型, 在其中定義的對應"
  - "TEXT 類型"
  - "TINT 類型"
  - "TSCHAR 類型"
  - "TUCHAR 類型"
  - "TXCHAR 類型"
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資料類型對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些資料型別的對應在 TCHAR.H 定義並視 `_UNICODE` 或 `_MBCS` 常數是否在程式中定義。  
  
 如需相關資訊，請參閱 [使用與 \_MBCS 程式碼的 TCHAR.H 資料型別](../text/using-tchar-h-data-types-with-mbcs-code.md)。  
  
### 泛用文字資料型別對應  
  
|泛型文字<br /><br /> 資料型別名稱|SBCS \(\_UNICODE,<br /><br /> \_MBCS not<br /><br /> 已定義的\)|\_MBCS<br /><br /> 已定義|\_UNICODE<br /><br /> 已定義|  
|---------------------|-------------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|  
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|  
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` 或 `_TEXT`|沒有作用 \(被前置處理器移除\)|沒有作用 \(被前置處理器移除\)|`L` \(將下列字元或字串轉換成其 Unicode 的對應\)|  
  
## 請參閱  
 [泛型文字對應](../c-runtime-library/generic-text-mappings.md)   
 [常數和全域變數對應](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [常式對應](../c-runtime-library/routine-mappings.md)   
 [泛型文字程式範例](../c-runtime-library/a-sample-generic-text-program.md)   
 [使用泛型文字對應](../c-runtime-library/using-generic-text-mappings.md)