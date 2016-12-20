---
title: "多載概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式多載，關於函式多載化"
  - "運算子多載，關於運算子多載"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 多載概觀
您可以使用 C\+\+ 語言多載函式和運算子。 「多載」\(Overloading\) 是一種作法，可將多個定義提供給相同範圍中指定的函式名稱。 編譯器會根據用於呼叫函式或運算子的引數來挑選正確版本的函式或運算子。 例如，最大函式即視為多載函式。 可用於如下列的程式碼：  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 在第一個函式呼叫中，會要求兩個類型為 `int` 之變數的最大值，呼叫的是 `max( int, int )` 函式。 不過，在第二個函式呼叫中，引數的類型是 `double`，因此會呼叫 `max( double, double )` 函式。  
  
## 請參閱  
 [多載 （c \+ \+）](../misc/overloading-cpp.md)