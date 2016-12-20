---
title: "編譯器錯誤 C3381 | Microsoft Docs"
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
  - "C3381"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3381"
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3381
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'assembly' : 組件存取規範只能適用於以 \/clr 選項編譯的程式碼  
  
 原生型別可以在組件之外看見，但您只能在 **\/clr** 編譯中指定原生型別的組件存取。  
  
 如需詳細資訊，請參閱[類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 範例  
 下列範例會產生 C3381。  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```