---
title: "編譯器錯誤 C2605 | Microsoft Docs"
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
  - "C2605"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2605"
ms.assetid: a0e6f132-5acf-4e19-b277-ddf196d182bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2605
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'name': 這個方法已保留在 Managed 或 WinRT 類別中  
  
 編譯器保留某些名稱供內部函式使用。  如需詳細資訊，請參閱[解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## 範例  
 下列範例會產生 C2605：  
  
```  
// C2605.cpp  
// compile with: /clr /c  
ref class R {  
protected:  
   void Finalize() {}   // C2605  
};  
```