---
title: "編譯器警告 (層級 3) C4800 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4800"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4800"
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 3) C4800
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 強制將 bool 的值定為 'true' 或 'false' \(效能警告\)  
  
 當不是 `bool` 的值被指派或強制設定為 `bool` 型別時，會產生此警告。  通常產生此訊息的原因，是因為將 `int` 變數指派給 `bool` 變數，而該 `int` 變數只包含 **true** 值與 **false** 值，因此可以重新宣告為型別 `bool`。  如果您無法重新撰寫運算式以使用型別 `bool`，您可以在運算式中加入 "`!=0`"，為運算式提供型別 `bool`。  根據設計，將運算式轉換為型別 `bool` 並不會關閉此警告。  
  
 下列範例會產生 C4800：  
  
```  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // try..  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```