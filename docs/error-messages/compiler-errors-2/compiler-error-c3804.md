---
title: 編譯器錯誤 C3804 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3804
dev_langs:
- C++
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0bd4d5921037094b3050e7a3c003b507a9cae4c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3804"></a>編譯器錯誤 C3804
'property_accessor': 存取子方法的屬性必須是全部靜態或全部非靜態  
  
 當定義非簡單式屬性，存取子函式可以是靜態或執行個體，但非兩者。  
  
 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md) 。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3804。  
  
```  
// C3804.cpp  
// compile with: /c /clr  
ref struct A {  
  
   property int i {  
      static int get() {}  
      void set(int i) {}  
   }   // C3804 error  
  
   // OK  
   property int j {  
      int get() { return 0; }  
      void set(int i) {}  
   }  
  
   property int k {  
      static int get() { return 0; }  
      static void set(int i) {}  
   }  
};  
```