---
title: 編譯器錯誤 C2598 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2598
dev_langs:
- C++
helpviewer_keywords:
- C2598
ms.assetid: 40777c62-39ba-441e-b081-f49f94b43547
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb41e0072f319c701f5f0cf13670a5f8f7051a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199388"
---
# <a name="compiler-error-c2598"></a>編譯器錯誤 C2598
連結規格必須在全域範圍  
  
 在本機的範圍中的連結規範宣告。  
  
 下列範例會產生 C2598:  
  
```  
// C2598.cpp  
// compile with: /c  
void func() {  
   extern "C" int func2();   // C2598  
}  
  
extern "C" int func( int i );  
```