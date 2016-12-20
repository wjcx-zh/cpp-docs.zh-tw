---
title: "編譯器錯誤 C3852 | Microsoft Docs"
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
  - "C3852"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3852"
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3852
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' \(擁有型別 'type'\)：彙總初始化無法初始化這個成員  
  
 已嘗試將預設的初始化 \(為彙總初始化的一部分\) 指定給無法在彙總初始化中接收預設初始化的資料成員。  
  
 下列範例會產生 C3852：  
  
```  
// C3852.cpp  
struct S  
{  
   short s;  
};  
  
struct S1  
{  
   int i;  
   const S s;  
};  
  
struct S2  
{  
   int i;  
   char & rc;  
};  
  
int main()  
{  
   S1 s1 = { 1 };   // C3852 const member   
   // try the following line instead  
   // S1 s1 = { 1, 2 };  
  
   S2 s2 = { 2 };   // C3852 reference member  
   // try the following line instead  
   // char c = 'a';  
   S2 s2 = { 2, c };  
}  
```