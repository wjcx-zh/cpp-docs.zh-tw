---
title: "編譯器警告 C4368 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4368
dev_langs: C++
helpviewer_keywords: C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9694eb05a2d14ff8dac49c0e9a3cb29dcf52bbac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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