---
title: "編譯器錯誤 C3288 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3288
dev_langs:
- C++
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9030ad9f46a36a1879d1c0f4f97b772e893b37ab
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3288"></a>編譯器錯誤 C3288
'type': 不合法取值 （dereference) 的控制代碼類型  
  
 編譯器偵測到不合法取值的控制代碼類型。 您可以控制代碼類型取值 （dereference），並將它指派為參考。 如需詳細資訊，請參閱[追蹤參考運算子](../../windows/tracking-reference-operator-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3288。  
  
```  
// C3288.cpp  
// compile with: /clr  
ref class R {};  
int main() {  
   *(System::Object^) nullptr;   // C3288  
  
// OK  
   (System::Object^) nullptr;   // OK  
   R^ r;  
   R% pr = *r;  
}  
```
