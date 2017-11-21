---
title: "編譯器錯誤 C2249 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2249
dev_langs: C++
helpviewer_keywords: C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5878c28ed0b4fc2663c17021aa9e277ccaa8ad4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2249"></a>編譯器錯誤 C2249
'member': 沒有可存取的路徑來存取成員宣告虛擬基底 'class' 中  
  
 `member`繼承自 nonpublic`virtual`基底類別或結構。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2249。  
  
```  
// C2249.cpp  
class A {  
private:  
   void privFunc( void ) {};  
public:  
   void pubFunc( void ) {};  
};  
  
class B : virtual public A {} b;  
  
int main() {  
   b.privFunc();    // C2249, private member of A  
   b.pubFunc();    // OK  
}  
```  
  
## <a name="example"></a>範例  
 如果您嘗試將資料流從 c + + 標準程式庫指派給另一個資料流，也會發生 C2249。  下列範例會產生 C2249。  
  
```  
// C2249_2.cpp  
#include <iostream>  
using namespace std;  
int main() {  
   cout = cerr;   // C2249  
   #define cout cerr;   // OK  
}  
```