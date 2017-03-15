---
title: "Based 指標 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__based"
  - "__based_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__based 關鍵字 [C++]"
  - "based 指標"
  - "指標, based"
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Based 指標 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 `__based` 關鍵字可讓您以指標為基礎 \(從現有指標位移的指標\) 宣告指標。  
  
## 語法  
  
```  
  
type __based( base ) declarator   
```  
  
## 備註  
 以指標位址為基礎的指標是 `__based` 關鍵字在 32 位元或 64 位元編譯中有效的唯一形式。  對於 Microsoft 32 位元 C\/C\+\+ 編譯器，基底指標是來自 32 位元指標基底的 32 位元位移。  在 64 位元環境中保留了一個類似的限制，其中基底指標是來自 64 位元基底的 64 位元位移。  
  
 以指標為基礎之指標的其中一項用途，就是包含指標的持續性識別項。  以指標為基礎的指標所組成的連結清單可以儲存至磁碟，然後以仍然有效的指標重新載入至記憶體中的另一個位置。  例如：  
  
```  
// based_pointers1.cpp  
// compile with: /c  
void *vpBuffer;  
struct llist_t {  
   void __based( vpBuffer ) *vpData;  
   struct llist_t __based( vpBuffer ) *llNext;  
};  
```  
  
 為指標 `vpBuffer` 所指派的記憶體位址，會在程式稍後的位置中進行配置。  連結清單會重新配置相對於 `vpBuffer` 的值。  
  
> [!NOTE]
>  包含指標的持續性識別項也可以藉由使用[記憶體對應檔案](http://msdn.microsoft.com/library/windows/desktop/aa366556)來達成。  
  
 對基底指標取值時，該基底必須透過宣告明確指定或以隱含方式得知。  
  
 為了與舊版相容，**\_based** 是 `__based` 的同義字。  
  
## 範例  
 下列程式碼示範如何變更其基底以變更基底指標。  
  
```  
// based_pointers2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int a1[] = { 1,2,3 };  
int a2[] = { 10,11,12 };  
int *pBased;  
  
typedef int __based(pBased) * pBasedPtr;  
  
using namespace std;  
int main() {  
   pBased = &a1[0];  
   pBasedPtr pb = 0;  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
  
   pBased = &a2[0];  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
}  
```  
  
  **1**  
**2**  
**10**  
**11**   
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [alloc\_text](../preprocessor/alloc-text.md)