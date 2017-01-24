---
title: "編譯器警告 (層級 4) C4202 | Microsoft Docs"
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
  - "C4202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4202"
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : '...': 名稱清單中的原型參數不合法  
  
 舊函式定義包含變數引數。  這些定義在 ANSI 相容性下會產生錯誤 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\)。  
  
## 範例  
  
```  
// C4202.c  
// compile with: /W4  
void func( a, b, ...)   // C4202  
int a, b;  
{}  
  
int main()  
{  
}  
```