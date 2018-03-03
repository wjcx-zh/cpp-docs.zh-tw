---
title: "編譯器警告 （層級 4） C4232 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0b8725ca2a7ee6c5f512559eecdb6b01ac4c6a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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