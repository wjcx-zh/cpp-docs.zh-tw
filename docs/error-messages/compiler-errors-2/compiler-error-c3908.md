---
title: 編譯器錯誤 C3908 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3908
dev_langs:
- C++
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f971ec355c3f1c3772b2a0cd4059cf0a8abd630
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3908"></a>編譯器錯誤 C3908
'construct' 比較不嚴格的存取層級  
  
 屬性存取子方法 （get 或 set） 不能有較不嚴格的存取權，指定屬性本身的存取。  同樣地，對於事件存取子方法。  
  
 如需詳細資訊，請參閱[屬性](../../windows/property-cpp-component-extensions.md)和[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下列範例會產生 C3908:  
  
```  
// C3908.cpp  
// compile with: /clr  
ref class X {  
protected:  
   property int i {  
   public:   // C3908 property i is protected   
      int get();  
   private:  
      void set(int);   // OK more restrictive  
   };  
};  
```