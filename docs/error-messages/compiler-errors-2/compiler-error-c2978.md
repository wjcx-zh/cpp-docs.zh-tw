---
title: "編譯器錯誤 C2978 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2978"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2978"
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2978
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤: 必須是 'keyword1' 或 'keyword２'，但找到的是類型 'keyword3'; 泛型中不支援非類型參數  
  
 泛型類別宣告不正確。 如需詳細資訊，請參閱[Generics](../../windows/generics-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C2978。  
  
```  
// C2978.cpp // compile with: /clr /c generic <ref class T>   // C2978 // try the following line instead // generic <typename T>   // OK ref class Utils { static void sort(T elems, size_t size); }; generic <int> // try the following line instead // generic <class T> ref class Utils2 { static void sort(T elems, size_t size); };  
```