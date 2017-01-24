---
title: "編譯器警告 C4368 | Microsoft Docs"
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
  - "C4368"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4368"
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4368
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法將 'member' 定義為 Managed 'type' 的成員: 不支援混合型別  
  
 您不能將原生資料成員嵌入 CLR 型別中。  
  
 不過您可以宣告原生型別的指標，並控制指標在建構函式和解構函式，以及 Managed 類別中的存留期 。  如需詳細資訊請參閱 [解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
 這項警告一律都以錯誤發出。  請使用 [warning](../../preprocessor/warning.md) Pragma 暫止 C4368。  
  
## 範例  
 下列範例會產生 C4368。  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```