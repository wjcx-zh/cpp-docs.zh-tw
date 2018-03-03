---
title: "編譯器錯誤 C3828 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3828
dev_langs:
- C++
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5925962e6e4f3792e431f0e86494a8402e30456b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3828"></a>編譯器錯誤 C3828
'object type': 正在建立的執行個體受管理時，不允許位置引數或 WinRTclasses  
  
 建立 managed 的類型或 Windows 執行階段類型的物件時，您無法使用運算子的位置形式[ref 新 gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md)或[新](../../cpp/new-operator-cpp.md)。  
  
 下列範例會產生 C3828，並示範如何修正此問題：  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```