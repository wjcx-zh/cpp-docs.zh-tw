---
title: "_bstr_t::operator +=、+ | Microsoft Docs"
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
  - "_bstr_t::operator+"
  - "_bstr_t::operator+="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "+ 運算子, _bstr_t 物件"
  - "+= 運算子, 附加字串"
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::operator +=、+
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將字元附加至 `_bstr_t` 物件的結尾或串連兩個字串。  
  
## 語法  
  
```  
  
      _bstr_t& operator+=(  
   const _bstr_t& s1   
);  
_bstr_t operator+(  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const char* s2,  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const wchar_t* s3,  
   const _bstr_t& s1   
);  
```  
  
#### 參數  
 *s1*  
 `_bstr_t` 物件。  
  
 *s2*  
 多位元組字串。  
  
 `s3`  
 Unicode 字串。  
  
## 備註  
 這些運算子會執行字串串連：  
  
-   **operator\+\=\(**  *s1*  **\)**：將 *s1* 的封裝 `BSTR` 中的字元附加至物件的封裝 `BSTR` 的結尾。  
  
-   **operator\+\(**  *s1*  **\)**：傳回新的 `_bstr_t`，這是由串連此物件及 *s1* 的 `BSTR` 組成。  
  
-   **operator\+\(**  *s2*  **&#124;**  *s1*  **\)**：傳回新的 `_bstr_t`，這是由串連多位元組字串 *s2* \(已轉換為 Unicode\) 及封裝在 *s1* 中的 `BSTR` 組成。  
  
-   **operator\+\(**  `s3` **,**  *s1*  **\)**：傳回新的 `_bstr_t`，這是由串連 Unicode 字串 `s3` 和封裝在 *s1* 中的 `BSTR` 組成。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)