---
title: "編譯器警告 （層級 1） C4369 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4369
dev_langs: C++
helpviewer_keywords: C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e3150b60de6019968680a5a7350f09868dd5564
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4369"></a>編譯器警告 (層級 1) C4369
'列舉值': 列舉值 'value' 無法表示為 'type'，值為 'new_value'  
  
 列舉值必須大於最大的值，指定基礎類型計算出來。  這會造成溢位，編譯器將列舉值包裝到最低的可能值類型。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4369。  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```