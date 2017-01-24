---
title: "編譯器錯誤 C2535 | Microsoft Docs"
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
  - "C2535"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2535"
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2535
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 已經定義或宣告成員函式  
  
 這項錯誤可能是由於在多載函式的多個定義或宣告中，使用了相同的型式參數清單 \(Formal Parameter List\) 所引起。  
  
 如果因處理函示而接到 C2535 錯誤訊息，請參閱 [解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) 以取得詳細資訊。  
  
 如果您打算編譯 ATL 專案，請參閱知識庫 \(Knowledge Base\) 文件 Q241852。  
  
 下列範例會產生 C2535：  
  
```  
// C2535.cpp  
// compile with: /c  
class C {  
public:  
   void func();   // forward declaration  
   void func() {}   // C2535  
};  
```