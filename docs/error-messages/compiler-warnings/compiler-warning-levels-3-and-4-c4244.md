---
title: "編譯器警告 （層級 3 和 4） C4244 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4244
dev_langs: C++
helpviewer_keywords: C4244
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc5fdcbced4da3fc4f40a6cbdfa319e026a0f1f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>編譯器警告 (層級 3 和 4) C4244
'conversion'：將 'type1' 轉換為 'type2'，資料可能遺失  
  
 整數類型會轉換為較小的整數類型。 如果這是層級 4 警告*type1*是`int`和*type2*小於`int`。 否則，它是層級 3 (指派類型的值[__int64](../../cpp/int8-int16-int32-int64.md)類型的變數至`unsigned int`)。 資料可能會遺失。  
  
 如果出現 C4244，您應變更程式以使用相容的類型，或在您的程式碼中加入某些邏輯，以確保可能值的範圍一定會與您所使用的類型相容。  
  
 C4244 也可能引發層級 2;請參閱[編譯器警告 （層級 2） C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md)如需詳細資訊。  
  
 轉換可能會因為隱含轉換而發生問題。  
  
 下列範例會產生 C4244：  
  
```  
// C4244_level4.cpp  
// compile with: /W4  
int aa;  
unsigned short bb;  
int main() {  
   int b = 0, c = 0;  
   short a = b + c;   // C4244  
  
   bb += c;   // C4244  
   bb = bb + c;   // C4244  
   bb += (unsigned short)aa;   // C4244  
   bb = bb + (unsigned short)aa;   // OK  
}  
```  
  
 如需詳細資訊，請參閱[一般算術轉換](../../c-language/usual-arithmetic-conversions.md)。  
  
```  
// C4244_level3.cpp  
// compile with: /W3  
int main() {  
   __int64 i = 8;  
   unsigned int ii = i;   // C4244  
}  
```  
  
 為 64 位元目標建置程式碼時，可能會發生為 32 位元目標建置時不會產生的警告 C4244。 以指標之間的差異為例，32 位元平台上的是 32 位元數量，但 64 位元平台上的會是 64 位元數量。  
  
 下列範例會在進行 64 位元目標的編譯時產生 C4244：  
  
```  
// C4244_level3_b.cpp  
// compile with: /W3   
int main() {  
   char* p1 = 0;  
   char* p2 = 0;  
   int x = p2 - p1;   // C4244  
}  
```