---
title: "編譯器錯誤 C3666 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3666
dev_langs:
- C++
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7a1456f1994e449139baff1ff8a35ab6187b209d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3666"></a>編譯器錯誤 C3666
'constructor': 覆寫規範 'keyword' 不允許在建構函式  
  
 在建構函式，使用了覆寫規範，並不允許。 如需詳細資訊，請參閱[覆寫規範](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3666。  
  
```  
// C3666.cpp  
// compile with: /clr /c  
ref struct R {  
   R() new {}   // C3666  
   R(int i) {}   // OK  
};  
```