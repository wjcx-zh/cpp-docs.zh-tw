---
title: "編譯器錯誤 C3223 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3223
dev_langs:
- C++
helpviewer_keywords:
- C3223
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 40d433c600dd560a4642aac1832fe94b60917fa0
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3223"></a>編譯器錯誤 C3223
'property' : 不可將 'typeid' 套用至屬性  
  
 您無法將 [typeid](../../windows/typeid-cpp-component-extensions.md) 套用至屬性。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3223。  
  
```  
// C3223.cpp  
// compile with: /clr  
ref class R {  
public:  
   property int myprop;  
};  
  
int main() {  
   System::Type^ type2 = R::myprop::typeid;   // C3223  
}  
```
