---
title: 編譯器錯誤 C2530 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b226ef5ca0e839c745e13d4118264a69ca408db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2530"></a>編譯器錯誤 C2530
'identifier': 必須初始化參考  
  
 您必須初始化參考它已宣告時，除非它已經宣告：  
  
-   以關鍵字[extern](../../cpp/using-extern-to-specify-linkage.md)。  
  
-   為類別、 結構或等位的成員 （以及它在建構函式中初始化）。  
  
-   做為函式宣告或定義的參數。  
  
-   為函式的傳回類型。  
  
 下列範例會產生 C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```