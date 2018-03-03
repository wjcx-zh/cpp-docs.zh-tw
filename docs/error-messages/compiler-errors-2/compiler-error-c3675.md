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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6545b7cfa8232ba8b48df104ce848eb34c0e108c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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