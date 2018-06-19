---
title: 編譯器錯誤 C2719 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2719
dev_langs:
- C++
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee8779db363c506d2f4ad884e15f78ba8231caa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233330"
---
# <a name="compiler-error-c2719"></a>編譯器錯誤 C2719
'parameter'：具有 __declspec(align('#')) 的型式參數不會對齊  
  
 [對齊](../../cpp/align-cpp.md)`__declspec`函式參數上不允許修飾詞。 函式參數對齊可藉由所使用的呼叫慣例來控制。 如需詳細資訊，請參閱[呼叫慣例](../../cpp/calling-conventions.md)。  
  
 下列範例會產生 C2719，並說明如何加以修正：  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```