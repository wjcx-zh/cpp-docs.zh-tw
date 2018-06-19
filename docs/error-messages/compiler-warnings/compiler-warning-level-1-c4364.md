---
title: 編譯器警告 （層級 1） C4364 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4364
dev_langs:
- C++
helpviewer_keywords:
- C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb3bfb8075d618a6d2ea9b733b01d8b456fdc0e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283757"
---
# <a name="compiler-warning-level-1-c4364"></a>編譯器警告 (層級 1) C4364
\#使用組件 'file' location(line_number) 沒有 as_friend 屬性，在先前看過因此未套用 as_friend  
  
 A`#using`指示詞重複指定的中繼資料檔案，但`as_friend`中第一個未使用限定詞，則編譯器會忽略第二個`as_friend`。  
  
 如需詳細資訊，請參閱[Friend 組件 （c + +）](../../dotnet/friend-assemblies-cpp.md)。  
  
## <a name="example"></a>範例  
 下列範例會建立元件。  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## <a name="example"></a>範例  
 下列範例會產生 C4364。  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```