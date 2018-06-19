---
title: 編譯器警告 （層級 4） C4429 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4429
dev_langs:
- C++
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00d4812fb1eefdd4364376288f063a6bf8b5dddf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293711"
---
# <a name="compiler-warning-level-4-c4429"></a>編譯器警告 (層級 4) C4429
可能不完整或格式不正確通用字元名稱  
  
 編譯器偵測到可能是格式不正確的通用字元名稱的字元序列。 通用字元名稱是`\u`後面接著四個十六進位數字，或`\U`後面八個十六進位數字。  
  
 下列範例會產生 C4429:  
  
```  
// C4429.cpp  
// compile with: /W4 /WX  
int \ug0e4 = 0;   // C4429  
// Try the following line instead:  
// int \u00e4 = 0;   // OK, a well-formed universal character name.  
```