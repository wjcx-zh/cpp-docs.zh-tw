---
title: "Managed 類型和 main 函式 (C++/CLI) | Microsoft Docs"
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
  - "main 函式, Managed 應用程式中"
  - "Managed 程式碼, main() 函式"
ms.assetid: 9d0e9620-58c4-4dac-a0e1-ffeb95f80fa5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Managed 類型和 main 函式 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在使用 **\/clr** 撰寫應用程式時，**main\(\)** 函式的引數不可以是 Managed 型別。  
  
 以下為適當簽章的範例：  
  
```  
// managed_types_and_main.cpp  
// compile with: /clr  
int main(int, char*[], char*[]) {}  
```  
  
## 請參閱  
 [Managed 類型](../dotnet/managed-types-cpp-cli.md)