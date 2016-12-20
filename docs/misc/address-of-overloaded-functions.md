---
title: "多載函式的位址 | Microsoft Docs"
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
  - "位址 [c + +]，多載函式"
  - "傳回多載位址 [c + +]"
  - "函式多載函式位址"
  - "這個指標多載函式"
ms.assetid: e7913e65-a295-445d-b2b0-1e60f8dfbc54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 多載函式的位址
若使用不帶引數的函式名稱，會傳回該函式的位址。 例如：  
  
```  
int Func( int i, int j );  
int Func( long l );  
  
...  
  
int (*pFunc) ( int, int ) = Func;  
```  
  
 在前述範例中，選取了 `Func` 的第一個版本，並將其位址複製到 `pFunc`。  
  
 編譯器會尋找帶引數清單且與目標引數清單完全相符的函式，以判斷應選取哪一個版本的函式。 編譯器會根據下列其中一個條件比對多載函式宣告中的引數：  
  
-   將初始化的物件 \(如前述範例所示\)  
  
-   指派陳述式的左側  
  
-   函式的型式引數  
  
-   使用者定義運算子的型式引數  
  
-   函式傳回類型  
  
 如果找不到完全相符的結果，採用函式位址的運算式即為模稜兩可的運算式，並會產生錯誤。  
  
 請注意，雖然 `Func` 是非成員函式，但在前述範例中，採用多載成員函式的位址時仍需遵守相同的規則。  
  
## 請參閱  
 [多載 （c \+ \+）](../misc/overloading-cpp.md)