---
title: "Compiler Error C2384 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2384"
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C2384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member'：無法將 \_\_declspec\(thread\) 套用至 Managed 或 WinRT 類別的成員  
  
 [執行緒](../../cpp/thread.md) `__declspec` 修飾詞無法使用於 Managed 或 Windows 執行階段類別的成員。  
  
 Managed 程式碼中的靜態執行緒區域儲存區僅可以使用於以靜態方式載入的 DLL — 在處理序啟動時 DLL 必須以靜態方式載入。  Windows 執行階段不支援執行緒區域儲存區。  
  
 下列範例會產生 C2384，並示範如何在 C\+\+\/CLI 程式碼中修正此問題：  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```