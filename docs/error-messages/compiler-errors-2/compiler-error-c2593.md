---
title: "編譯器錯誤 C2593 | Microsoft Docs"
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
  - "C2593"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2593"
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2593
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator identifier' 模稜兩可  
  
 對多載運算子定義了一個以上可能的運算子。  
  
 如果您在一個或多個實質參數上使用明確轉型，可能會修正這項錯誤。  
  
 下列範例會產生 C2593：  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 這項錯誤可能會因為使用 `CArchive` 物件序列化浮點變數而產生。  編譯器認為 `<<` 運算子模稜兩可。  `CArchive` 唯一可序列化的基本 C\+\+ 型別是固定大小的型別 `BYTE`、`WORD`、`DWORD` 和 `LONG`。  所有整數型別都必須轉型為上述其中一種型別，才能進行序列化。  浮點型別必須使用 `CArchive::Write()` 成員函式加以封存。  
  
 下列範例顯示將浮點變數 \(`f`\) 保存至 `ar` 的方式：  
  
```  
ar.Write(&f, sizeof( float ));  
```