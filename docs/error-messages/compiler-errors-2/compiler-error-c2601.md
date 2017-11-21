---
title: "編譯器錯誤 C2601 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2601
dev_langs: C++
helpviewer_keywords: C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cdffa40b751232525920d1d92affd9e3778d2f61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2601"></a>編譯器錯誤 C2601
'function': 區域函式定義不合法  
  
 程式碼會嘗試在函式的函式定義。  
  
 或者，您之前 C2601 錯誤位置的原始程式碼中可能有額外的括號。  
  
 下列範例會產生 C2601:  
  
```  
// C2601.cpp  
int main() {  
   int i = 0;  
  
   void funcname(int j) {   // C2601  
      j++;  
   }  
}  
```