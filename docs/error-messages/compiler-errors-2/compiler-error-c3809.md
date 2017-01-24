---
title: "編譯器錯誤 C3809 | Microsoft Docs"
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
  - "C3809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3809"
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3809
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class'：Managed 或 WinRT 類型不可以有任何的 friend 函式\/類別\/介面  
  
 Managed 類型和 Windows 執行階段類型不允許 friends。  若要修正這個錯誤，請不要在 Managed 或 Windows 執行階段類型中宣告 friends。  
  
 下列範例會產生 C3809：  
  
```  
// C3809a.cpp  
// compile with: /clr  
ref class A {};  
  
ref class B  
{  
public:  
   friend ref class A;   // C3809  
};  
  
int main()  
{  
}  
```