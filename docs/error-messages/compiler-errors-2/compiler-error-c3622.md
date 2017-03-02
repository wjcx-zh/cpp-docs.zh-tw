---
title: "編譯器錯誤 C3622 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3622
dev_langs:
- C++
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ed81cc21e3c3ae574a0c83a692f75638d24111de
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3622"></a>編譯器錯誤 C3622
'class': 類別宣告為 '關鍵字' 無法具現化  
  
嘗試將類別標示為具現化[抽象](../../windows/abstract-cpp-component-extensions.md)。 類別標記為`abstract`可做為基底類別，但它無法具現化。  
  
## <a name="example"></a>範例  
下列範例會產生 C3622。  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  

