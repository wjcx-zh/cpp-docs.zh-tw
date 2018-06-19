---
title: 編譯器警告 （層級 1） C4068 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4068
dev_langs:
- C++
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37860067c8ff5409fd4376638ef1754673bca93b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279405"
---
# <a name="compiler-warning-level-1-c4068"></a>編譯器警告 (層級 1) C4068
未知的 pragma  
  
 編譯器已忽略無法辨識的 [pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。 請確認您使用的編譯器允許 **pragma** 。 下列範例會產生 C4068：  
  
```  
// C4068.cpp  
// compile with: /W1  
#pragma NotAValidPragmaName   // C4068, use valid name to resolve  
int main()  
{  
}  
```