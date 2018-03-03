---
title: "編譯器錯誤 C2506 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2506
dev_langs:
- C++
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d084e04e90c7fce9756e72a8b19d566ee829287
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2506"></a>編譯器錯誤 C2506
'member': '__declspec(modifier)' 無法套用至這個符號  
  
 您無法宣告每個處理程序或每個 appdomain 的 managed 類別的靜態成員。  
  
 如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2506。  
  
```  
// C2506.cpp  
// compile with: /clr /c  
ref struct R {  
   __declspec(process) static int n;   // C2506  
   int o;   // OK  
};  
```