---
title: "Naked 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "終解程式碼"
  - "函式 [C++], naked"
  - "naked 函式"
  - "初構程式碼"
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Naked 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `naked` 儲存類別屬性是 Microsoft 專有的 C 語言擴充功能。  針對以 `naked` 儲存類別屬性宣告的函式，編譯器會產生不具初構和終解程式碼的程式碼。  利用此功能就可以使用內嵌組合語言程式碼撰寫您自己的初構\/終解程式碼序列。  naked 函式在撰寫虛擬裝置驅動程式方面特別實用。  
  
 由於 `naked` 屬性僅與函式定義相關，而且不是類型修飾詞，因此 naked 函式會使用[擴充儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)中所述的擴充屬性語法。  
  
 下列範例會定義具有 `naked` 屬性的函式：  
  
```  
__declspec( naked ) int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 或者：  
  
```  
#define Naked   __declspec( naked )  
  
Naked int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 `naked` 屬性只會影響編譯器針對函式的初構和終解序列產生程式碼的本質。  它不會影響針對呼叫這類函式所產生的程式碼。  因此，`naked` 屬性不會視為函式類型的一部分，而且函式指標不能有 `naked` 屬性。  此外，`naked` 屬性無法套用至資料定義。  例如，下列程式碼會產生錯誤：  
  
```  
__declspec( naked ) int i;  /* Error--naked attribute not */  
                            /* permitted on data declarations. */  
```  
  
 `naked` 屬性只與函式的定義相關，而且無法在函式的原型中指定。  下列宣告會產生編譯器錯誤：  
  
```  
__declspec( naked ) int func();   /* Error--naked attribute not */  
                     /* permitted on function declarations.    */   \  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [C 函式定義](../c-language/c-function-definitions.md)