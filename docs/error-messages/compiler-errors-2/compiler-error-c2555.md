---
title: "編譯器錯誤 C2555 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2555"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2555"
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2555
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

class1::function1': 覆寫虛擬函式傳回型別不同而且不是來自 'class2::function2' 的 Covariant  
  
 虛擬函式和衍生覆寫函式具有相同的參數清單，但傳回型別不同。  衍生類別內的覆寫函式不能僅使用它的傳回型別，來與基底類別內的虛擬函式區隔。  
  
 若要解決這個錯誤，請在呼叫虛擬函式後，轉換 \(Cast\) 傳回值。  
  
 如果使用 \/clr 編譯，您也可能會看到這項錯誤。例如，Visual C\+\+ 的對等用法如下列 C\# 宣告：  
  
```  
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);  
```  
  
 是  
  
```  
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];  
```  
  
 如需 C2555 的詳細資訊，請參閱知識庫文件 Q240862。  
  
 下列範例會產生 C2555：  
  
```  
// C2555.cpp  
// compile with: /c  
struct X {  
   virtual void func();  
};  
struct Y : X {  
   char func();  // C2555  
   void func2();   // OK  
};  
```