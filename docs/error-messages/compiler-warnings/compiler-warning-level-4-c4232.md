---
title: 編譯器警告 （層級 4） C4232 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 093f9eeeb27b402b58f3d53ae34952c34dca3779
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4232"></a>編譯器警告 (層級 4) C4232
使用非標準擴充: 'identifier': dllimport 'dllimport' 的位址並非靜態，不保證唯一  
  
 Microsoft 擴充功能 (/Ze) 下您可以授與非靜態值與宣告的函式位址**dllimport**修飾詞。 在 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，這會導致錯誤。  
  
 下列範例會產生 C4232:  
  
```  
// C4232.c  
// compile with: /W4 /Ze /c  
int __declspec(dllimport) f();  
int (*pfunc)() = &f;   // C4232  
```