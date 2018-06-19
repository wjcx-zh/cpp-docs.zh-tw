---
title: 編譯器錯誤 C2142 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2142
dev_langs:
- C++
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11fd3cd62b236daa93424f53a0896888a89fe33d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170394"
---
# <a name="compiler-error-c2142"></a>編譯器錯誤 C2142
函式宣告不同，只能在其中一個指定的變數參數  
  
 此函式的一個宣告包含變數參數清單。 卻不符合另一個宣告。 ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 只。  
  
 下列範例會產生 C2142:  
  
```  
// C2142.c  
// compile with: /Za /c  
void func();  
void func( int, ... );   // C2142  
void func2( int, ... );   // OK  
```