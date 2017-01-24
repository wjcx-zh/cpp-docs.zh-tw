---
title: "_bstr_t::wchar_t*、_bstr_t::char* | Microsoft Docs"
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
  - "_bstr_t::wchar_t*"
  - "_bstr_t::char*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "運算子 char*"
  - "運算子 wchar_t*"
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::wchar_t*、_bstr_t::char*
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 BSTR 字元做為窄字元或寬字元陣列傳回。  
  
## 語法  
  
```  
  
      operator const wchar_t*( ) const throw( );   
operator wchar_t*( ) const throw( );   
operator const char*( ) const;   
operator char*( ) const;  
```  
  
## 備註  
 這些運算子可用來擷取 `BSTR` 物件所封裝的字元資料。  指派新值給傳回的指標並不會修改原始 BSTR 資料。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)