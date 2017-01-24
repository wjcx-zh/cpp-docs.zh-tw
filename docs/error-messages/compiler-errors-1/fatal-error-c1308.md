---
title: "嚴重錯誤 C1308 | Microsoft Docs"
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
  - "C1308"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1308"
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1308
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支援所連結的組件  
  
 .netmodule 允許做為連結器的輸入，但組件則不被允許。  當嘗試連結一個以 `/clr:safe` 編譯的組件時，可能會產生這個錯誤。  
  
 如需詳細資訊，請參閱 [.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)。  
  
 下列範例會產生 C1308：  
  
```  
// C1308.cpp  
// compile with: /clr:safe /LD  
public ref class MyClass {  
public:  
   int i;  
};  
```  
  
 然後，  
  
```  
// C1308b.cpp  
// compile with: /clr /link C1308b.obj C1308.dll  
// C1308 expected  
#using "C1308.dll"  
int main() {  
   MyClass ^ my = gcnew MyClass();  
}  
```