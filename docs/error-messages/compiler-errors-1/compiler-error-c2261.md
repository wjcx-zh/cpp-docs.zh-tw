---
title: 編譯器錯誤 C2261 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45050daf3149cd813fb23b5814be5fe49c375f03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170462"
---
# <a name="compiler-error-c2261"></a>編譯器錯誤 C2261
'string': 組件參考無效，無法解析  
  
 值不是有效的。  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 用來指定 friend 組件。 例如，如果 a.dll 想要指定 b.dll 做為 friend 組件，您會指定 （以 a.dll): InternalsVisibleTo("b")。 然後，執行階段可讓 b.dll 存取 a.dll （除了私用類型） 中的所有項目。  
  
 如需指定 friend 組件時的正確語法的詳細資訊，請參閱[Friend 組件 （c + +）](../../dotnet/friend-assemblies-cpp.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2261。  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```