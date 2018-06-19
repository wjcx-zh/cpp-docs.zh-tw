---
title: 編譯器警告 C4368 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4368
dev_langs:
- C++
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3a7e53c979a3b13bde205a4546c486061a17110
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270492"
---
# <a name="compiler-warning-c4368"></a>編譯器警告 C4368
無法定義 managed 'type' 的成員 'member': 不支援混合的類型  
  
 您無法內嵌原生資料成員中的 CLR 型別。  
  
 不過您可以宣告原生類型的指標，並控制指標在 Managed 類別建構函式和解構函式與完成項中的存留期。 如需詳細資訊，請參閱[解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
 為錯誤，永遠會發出這個警告。 使用[警告](../../preprocessor/warning.md)pragma 來停用 C4368。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4368。  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```