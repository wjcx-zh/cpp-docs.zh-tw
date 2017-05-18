---
title: "編譯器警告 （層級 3） C4398 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 18270bb89bcc5d1855750c572a5b6fb9e51c2ba3
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4398"></a>編譯器警告 (層級 3) C4398
'variable': 每個處理程序的全域物件可能無法正常運作具有多個 appdomain。請考慮使用 __declspec(appdomain)  
  
 虛擬函式與[__clrcall](../../cpp/clrcall.md)呼叫慣例在原生型別會建立每個應用程式網域 vtable。 使用多個應用程式定義域中時，這類變數可能無法正確地修正。  
  
 您可以明確地標示變數來解決這個警告`__declspec(appdomain)`。 在 Visual Studio 2017 之前的 Visual Studio 版本中，您可以解決這個警告使用編譯**/clr: pure**，因此依預設每個 appdomain 全域變數。  
  
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
