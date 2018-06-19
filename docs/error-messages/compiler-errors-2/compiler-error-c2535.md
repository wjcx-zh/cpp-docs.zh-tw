---
title: 編譯器錯誤 C2535 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dc791cd7782cc758aa51b0c61d87a79570c13c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229552"
---
# <a name="compiler-error-c2535"></a>編譯器錯誤 C2535
'identifier': 已經定義或宣告的成員函式  
  
 這個錯誤可能被因使用一個以上的定義或宣告的多載函式中相同的型式參數清單。  
  
 如果您因 c2535 Dispose 函式，請參閱[解構函式與完成項](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)如需詳細資訊。  
  
 如果您正在編譯 ATL 專案，請參閱知識庫文章 Q241852。  
  
 下列範例會產生 C2535:  
  
```  
// C2535.cpp  
// compile with: /c  
class C {  
public:  
   void func();   // forward declaration  
   void func() {}   // C2535  
};  
```