---
title: "編譯器錯誤 C3282 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3282
dev_langs: C++
helpviewer_keywords: C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ec105274aa4a2aabc806e21731dcdea930b08e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3282"></a>編譯器錯誤 C3282
泛型參數清單只能出現在受管理或 WinRTclasses、 結構或函式  
  
 使用泛型參數清單的方式錯誤。  如需詳細資訊，請參閱[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3282，並示範如何修正此問題。  
  
```  
// C3282.cpp  
// compile with: /clr /c  
generic <typename T> int x;   // C3282  
  
ref struct GC0 {  
   generic <typename T> int x;   // C3282  
};  
  
// OK  
generic <typename T>  
ref class M {};  
```