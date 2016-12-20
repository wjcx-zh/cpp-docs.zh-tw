---
title: "編譯器錯誤 C2521 | Microsoft Docs"
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
  - "C2521"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2521"
ms.assetid: 6042821b-e345-4a54-a7e9-a2c9019ea016
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2521
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

function 不接受任何引數  
  
 您試圖在解構函式 \(Destructor\) 或完成項上使用引數。  
  
 如需詳細資訊，請參閱 [解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
## 範例  
 下列範例會產生 C2521。  
  
```  
// C2521.cpp  
// compile with: /clr  
ref class R {  
protected:  
   !R() {}  
  
public:  
   void CleanUp() {  
      this->!R(4);   // C2521  
      this->!R();   // OK  
   }  
};  
  
int main() {  
   R^ r = gcnew R();  
   r->CleanUp();  
}  
```