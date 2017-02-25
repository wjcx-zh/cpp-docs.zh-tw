---
title: "定義和宣告 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "匯出函式"
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 定義和宣告 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 DLL 介面會參考已知由系統中某些程式匯出的所有項目 \(函式和資料\)，也就是宣告為 **dllimport** 或 `dllexport` 的所有項目。  DLL 介面中的所有宣告都必須指定 **dllimport** 或 `dllexport` 屬性。  不過，此定義只能指定 `dllexport` 屬性。  例如，下列函式定義會產生編譯器錯誤：  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int func()    /* Error; dllimport prohibited in */  
                        /* definition. */  
{  
   return 1;  
}  
```  
  
 此程式碼也會產生錯誤：  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int i = 10;      /* Error; this is a definition. */  
```  
  
 不過，這個語法是正確的：  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport int i = 10;      /* Okay: this is an export definition. */  
```  
  
 使用 `dllexport` 隱含了定義，而 **dllimport** 則隱含了宣告。  您必須使用 `extern` 關鍵字搭配 `dllexport` 以強制進行宣告，否則其中會隱含宣告。  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
extern DllImport int k;   /* These are correct and imply */  
Dllimport int j;          /* a declaration. */      
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [DLL 匯入及匯出函式](../c-language/dll-import-and-export-functions.md)