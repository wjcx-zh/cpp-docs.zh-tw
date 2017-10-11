---
title: "編譯器警告 （層級 1） C4010 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b6a0c84d5138cf2ae8a7a6279d9dc0fde9fe9512
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-level-1-c4010"></a>編譯器警告 （層級 1） C4010
單行註解包含行接續字元  
  
 單行註解，導入的 / /，您也可以包含反斜線 (\\) 做為行接續字元。 編譯器會考慮接續的下一行，並將它視為註解。  
  
 部分語法導向編輯器並不表示成註解的接續字元的下一行。 忽略任何會導致此警告的程式行著色的語法。  
  
 下列範例會產生 C4010:  
  
```  
// C4010.cpp  
// compile with: /WX  
int main() {  
   // the next line is also a comment because of the backslash \  
   int a = 3; // C4010  
   a++;  
}  
```
