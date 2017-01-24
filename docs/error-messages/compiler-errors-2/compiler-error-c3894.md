---
title: "編譯器錯誤 C3894 | Microsoft Docs"
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
  - "C3894"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3894"
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3894
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : initonly 靜態資料成員的左值使用只允許出現在類別 'class' 的類別建構函式中  
  
 靜態 [initonly](../../dotnet/initonly-cpp-cli.md) 資料成員只能在其宣告點上或靜態建構函式中用來做為左值。  
  
 執行個體 \(非靜態\) initonly 資料成員只能在其宣告點上或執行個體 \(非靜態\) 建構函式中用來做為左值。  
  
 下列範例會產生 C3894：  
  
```  
// C3894.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly static int data_var = 0;  
  
public:  
   // class constructor  
   static Y1() {  
      data_var = 99;   // OK  
      System::Console::WriteLine("in static constructor");  
   }  
  
   // not the class constructor  
   Y1(int i) {  
      data_var = i;   // C3894  
   }  
  
   static void Test() {}  
  
};  
  
int main() {  
   Y1::data_var = 88;   // C3894  
   int i = Y1::data_var;  
   Y1 ^ MyY1 = gcnew Y1(99);  
   Y1::Test();  
}  
```