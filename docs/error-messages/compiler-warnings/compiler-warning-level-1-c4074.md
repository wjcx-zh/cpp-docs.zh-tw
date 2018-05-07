---
title: 編譯器警告 （層級 1） C4074 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4074
dev_langs:
- C++
helpviewer_keywords:
- C4074
ms.assetid: cd510e66-c338-4a86-a4d7-bfa1df9b16c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9072728660ca78097a1e36e492670a614bb2b2f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4074"></a>編譯器警告 （層級 1） C4074
初始設定式置於編譯器保留的初始化區域  
  
 所指定的編譯器初始化區域[#pragma init_seg](../../preprocessor/init-seg.md)，已保留給 Microsoft。 此區域中的程式碼在執行之前初始化的 C 執行階段程式庫。  
  
 下列範例會產生 C4074:  
  
```  
// C4074.cpp  
// compile with: /W1  
#pragma init_seg( compiler )   // C4074  
  
// try this line to resolve the warning  
// #pragma init_seg(user)  
  
int main() {  
}  
```