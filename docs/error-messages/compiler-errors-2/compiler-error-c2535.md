---
title: "編譯器錯誤 C2535 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cdcd4aa00f0b96e0995e7589a8bbe4d1b990c74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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