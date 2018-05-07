---
title: 編譯器警告 （層級 1） C4326 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4326
dev_langs:
- C++
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 838c79d6ba897905dad18788adc5ee682ff2fa2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4326"></a>編譯器警告 (層級 1) C4326
'function' 傳回型別應該是 'type1'，而不是 'type2'  
  
 函式傳回型別以外***type1***。 例如，使用[/Za](../../build/reference/za-ze-disable-language-extensions.md)，main 未傳回`int`。  
  
 下列範例會產生 C4326:  
  
```  
// C4326.cpp  
// compile with: /Za /W1  
char main()  
{   // C4326 try int main  
}  
```