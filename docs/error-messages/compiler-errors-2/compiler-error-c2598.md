---
title: "編譯器錯誤 C2598 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2598
dev_langs: C++
helpviewer_keywords: C2598
ms.assetid: 40777c62-39ba-441e-b081-f49f94b43547
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7d0d5a5e48ada3ac504fb12c5239d061761ce016
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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