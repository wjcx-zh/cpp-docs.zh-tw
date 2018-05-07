---
title: 編譯器警告 （層級 3） C4398 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ace2df75b5d2579b66a4d3930470021726ba4c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4398"></a>編譯器警告 (層級 3) C4398
'variable': 處理序專屬全域物件可能無法與多個 appdomain; 正常運作請考慮使用 __declspec(appdomain)  
  
 虛擬函式與[__clrcall](../../cpp/clrcall.md)原生類型中呼叫慣例會導致建立每個應用程式網域 vtable。 使用多個應用程式定義域中時，這類變數可能無法正確地修正。  
  
 您可以明確地標示變數來解決這個警告`__declspec(appdomain)`。 在 Visual Studio 2017 之前的 Visual Studio 版本中，您可以解決這個警告編譯 **/clr: pure**，讓預設 appdomain 的全域變數。  
  
 如需詳細資訊，請參閱[appdomain](../../cpp/appdomain.md)和[應用程式定義域和 Visual c + +](../../dotnet/application-domains-and-visual-cpp.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4398。  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```