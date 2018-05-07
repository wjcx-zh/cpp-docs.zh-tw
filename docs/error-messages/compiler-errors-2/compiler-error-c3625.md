---
title: 編譯器錯誤 C3625 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3625
dev_langs:
- C++
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a3462c3600a59c453fbde818c11b602c2254343
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3625"></a>編譯器錯誤 C3625
'native_type'：不可以從 Managed 或 WinRT 類型 'type' 衍生原生類型  
  
原生類別不可繼承自 Managed 或 WinRT 類別。 如需詳細資訊，請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3625：  
  
```  
// C3625.cpp  
// compile with: /clr /c  
ref class B {};  
class D : public B {};   // C3625 cannot inherit from a managed class  
```  
