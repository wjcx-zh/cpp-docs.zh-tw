---
title: "編譯器錯誤 C2085 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5834cbca32c2e3bb0c20ab39ee5d3b9d3e8e9c55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2085"></a>編譯器錯誤 C2085
'identifier': 不在型式參數清單  
  
 函式定義中，但不是在型式參數清單中，已宣告的識別項。 (ANSI C)  
  
 下列範例會產生 C2085:  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 可能的解決方式：  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 使用分號遺漏`func1()`看起來像函式定義不原型，因此`main`內定義`func1()`，產生的識別項的錯誤 C2085 `main`。