---
title: "編譯器錯誤 C2144 | Microsoft Docs"
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
  - "C2144"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2144"
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2144
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

語法錯誤 : 'type' 必須在 'token' 之後  
  
 編譯器預期會有 `token`，但卻找到 `type`。  
  
 這項錯誤可能是因為遺漏右邊的大括號、右括號，或分號而產生。  
  
 嘗試從包含泛空白字元的 CLR 關鍵字建立巨集時，也可能會發生 C2144。  
  
 如果您正嘗試要做型別轉送，也可以參閱 C2144。  如需詳細資訊，請參閱[Type Forwarding \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C2144。  
  
```  
// C2144.cpp  
// compile with: /clr /c  
#define REF ref  
REF struct MyStruct0;   // C2144  
  
// OK  
#define REF1 ref struct  
REF1 MyStruct1;  
```  
  
## 範例  
 下列範例會產生 C2144。  
  
```  
// C2144_2.cpp  
// compile with: /clr /c  
ref struct X {  
  
   property double MultiDimProp[,,] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp[int , int, int] {  
      double get(int, int, int) { return 1; }  
      void set(int i, int j, int k, double l) {}  
   }  
  
   property double MultiDimProp2[] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp2[int] {  
      double get(int) { return 1; }  
      void set(int i, double l) {}  
   }  
};  
```