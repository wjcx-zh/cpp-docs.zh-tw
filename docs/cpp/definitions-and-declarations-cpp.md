---
title: "定義和宣告 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 定義和宣告 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 DLL 介面會參考已知由系統中某些程式匯出的所有項目 \(函式和資料\)，也就是宣告為 **dllimport** 或 `dllexport` 的所有項目。  DLL 介面中的所有宣告都必須指定 **dllimport** 或 `dllexport` 屬性。  不過，此定義只能指定 `dllexport` 屬性。  例如，下列函式定義會產生編譯器錯誤：  
  
```  
__declspec( dllimport ) int func() {   // Error; dllimport  
                                    // prohibited on definition.  
   return 1;  
}  
```  
  
 此程式碼也會產生錯誤：  
  
```  
#define DllImport   __declspec( dllimport )  
  
__declspec( dllimport ) int i = 10;  // Error; this is a  
                                     // definition.  
```  
  
 不過，這個語法是正確的：  
  
```  
__declspec( dllexport ) int i = 10;     // Okay--export definition  
```  
  
 使用 `dllexport` 隱含了定義，而 **dllimport** 則隱含了宣告。  您必須使用 `extern` 關鍵字搭配 `dllexport` 以強制進行宣告，否則其中會隱含宣告。  因此，下列範例是正確的：  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
extern DllImport int k; // These are both correct and imply a  
DllImport int j;        // declaration.  
```  
  
 下列範例釐清前述範例：  
  
```  
static __declspec( dllimport ) int l; // Error; not declared extern.  
  
void func() {  
    static __declspec( dllimport ) int s;  // Error; not declared  
                                           // extern.  
    __declspec( dllimport ) int m;         // Okay; this is a   
                                           // declaration.  
    __declspec( dllexport ) int n;         // Error; implies external  
                                           // definition in local scope.  
    extern __declspec( dllimport ) int i;  // Okay; this is a  
                                           // declaration.  
    extern __declspec( dllexport ) int k;  // Okay; extern implies  
                                           // declaration.  
    __declspec( dllexport ) int x = 5;     // Error; implies external  
                                           // definition in local scope.  
}  
```  
  
## END Microsoft 特定的  
  
## 請參閱  
 [dllexport、dllimport](../cpp/dllexport-dllimport.md)