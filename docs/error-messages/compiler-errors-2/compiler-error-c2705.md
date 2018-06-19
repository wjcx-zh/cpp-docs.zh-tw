---
title: 編譯器錯誤 C2705 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2705
dev_langs:
- C++
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dce6bdb0a5c20fbe54b04eaf83ee8f90427017c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235451"
---
# <a name="compiler-error-c2705"></a>編譯器錯誤 C2705
'label': 不合法的跳躍進入 '例外狀況處理常式區塊' 範圍  
  
 執行會跳至標籤內`try` / `catch`， `__try` / `__except`， `__try` / `__finally`區塊。 如需詳細資訊，請參閱[例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。  
  
 下列範例會產生 C2705:  
  
```  
// C2705.cpp  
int main() {  
goto trouble;  
   __try {  
      trouble: ;   // C2705  
   }  
   __finally {}  
  
   // try the following line instead  
   // trouble: ;  
}  
```