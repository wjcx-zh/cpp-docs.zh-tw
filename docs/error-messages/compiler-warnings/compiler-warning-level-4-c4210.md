---
title: "編譯器警告 (層級 4) C4210 | Microsoft Docs"
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
  - "C4210"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4210"
ms.assetid: f8600adf-dfe2-4022-a37a-3d4997641dfd
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4210
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：給函式檔案範圍  
  
 使用預設的 Microsoft 擴充功能 \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\)，函式宣告具有檔案範圍。  
  
```  
// C4210.c  
// compile with: /W4 /c  
void func1()  
{  
   extern int func2( double );   // C4210 expected  
}  
  
int main()  
{  
   func2( 4 );   //  /Ze passes 4 as type double  
}                //  /Za passes 4 as type int  
```  
  
 此擴充可避免您的程式碼被帶到其他編譯器。