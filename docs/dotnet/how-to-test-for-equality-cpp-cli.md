---
title: "如何：測試是否相等 (C++/CLI) | Microsoft Docs"
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
helpviewer_keywords: 
  - "相等, 測試"
ms.assetid: 9115e298-9f75-452d-bdfb-6eeb0fa0b3c6
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：測試是否相等 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在下列範例中，使用 Managed Extensions for C\+\+ 的相等測試會根據控制代碼所參考的內容來進行。  
  
## 範例  
  
```  
// mcppv2_equality_test.cpp  
// compile with: /clr /LD  
using namespace System;  
  
bool Test1() {  
   String ^ str1 = "test";  
   String ^ str2 = "test";  
   return (str1 == str2);  
}  
```  
  
 這個程式的 IL 顯示傳回值是藉由使用 op\_Equality 呼叫來實作。  
  
```  
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,  
                                                               string)  
```  
  
## 請參閱  
 [Managed 類型](../dotnet/managed-types-cpp-cli.md)