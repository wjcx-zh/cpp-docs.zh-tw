---
title: "編譯器錯誤 C2702 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2702
dev_langs:
- C++
helpviewer_keywords:
- C2702
ms.assetid: 6def15d4-9a8d-43e7-ae35-42d7cb57c27e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9bf76f5f48b781c51bcf219f398e071a09f290d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2702"></a>編譯器錯誤 C2702
__except 不可以出現在終止區塊中  
  
 例外狀況處理常式 (`__try`/`__except`) 無法在巢狀`__finally`區塊。  
  
 下列範例會產生 C2702:  
  
```  
// C2702.cpp  
// processor: x86 IPF  
int Counter;  
int main() {  
   __try {}  
   __finally {  
      __try {}   // C2702  
      __except( Counter ) {}   // C2702  
   }  
}  
```