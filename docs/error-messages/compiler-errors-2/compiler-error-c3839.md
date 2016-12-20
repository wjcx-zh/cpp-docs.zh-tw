---
title: "編譯器錯誤 C3839 | Microsoft Docs"
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
  - "C3839"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3839"
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3839
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法變更 managed 或 WinRT 類型中的對齊  
  
 managed 或 Windows 執行階段類型中的變數對齊由 CLR 或 Windows 執行階段所控制，而且無法利用[對齊](../../cpp/align-cpp.md)修改。  
  
 下列範例會產生 C3839：  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
  
```