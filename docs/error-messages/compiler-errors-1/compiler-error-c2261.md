---
title: "編譯器錯誤 C2261 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2261
dev_langs: C++
helpviewer_keywords: C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8269b891ed899501625973b81c1823d4db2d56c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2261"></a>編譯器錯誤 C2261
'string': 組件參考無效，無法解析  
  
 值不是有效的。  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>用來指定 friend 組件。 例如，如果 a.dll 想要指定 b.dll 做為 friend 組件，您會指定 （以 a.dll): InternalsVisibleTo("b")。 然後，執行階段可讓 b.dll 存取 a.dll （除了私用類型） 中的所有項目。  
  
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