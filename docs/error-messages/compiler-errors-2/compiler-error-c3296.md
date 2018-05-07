---
title: 編譯器錯誤 C3296 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3296
dev_langs:
- C++
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85b4f80a9f257fa5e5d9ed8701a6ee7cfdf68cfd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3296"></a>編譯器錯誤 C3296
'property': 已經有這個名稱的屬性  
  
 編譯器遇到具有相同名稱的多個屬性。 類型中的每個屬性都必須具有唯一的名稱。  
  
 如需詳細資訊，請參閱 [property](../../windows/property-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3296。  
  
```  
// C3296.cpp  
// compile with: /clr /c  
using namespace System;  
  
ref class R {  
public:  
   property int MyProp[int] { int get(int); }  
  
   property String^ MyProp[int] { void set(int, String^); }   // C3296  
};  
```