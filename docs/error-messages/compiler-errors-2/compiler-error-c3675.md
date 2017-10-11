---
title: "編譯器錯誤 C3675 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d45236fc32fd0d10e9617b6946683d8ebd73ef0e
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3675"></a>編譯器錯誤 C3675
'function': 已保留，因為 'property' 定義  
  
 當您宣告簡單的屬性時，則編譯器會產生的 get 和 set 存取子方法，以及這些名稱會出現在您程式的範圍。  編譯器產生的名稱的格式 get_ 和 set_ 屬性名稱前面加上。  因此，您無法宣告具有相同名稱做為編譯器產生的存取子函式。  
  
 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3675。  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```
