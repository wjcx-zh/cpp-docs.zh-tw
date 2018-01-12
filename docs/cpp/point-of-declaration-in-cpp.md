---
title: "C + + 中宣告點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64c1fa1d6d8feb4b869957101bb4b37f125d0f8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="point-of-declaration-in-c"></a>C++ 中的宣告點
名稱會視為在緊接著它的宣告子之後、但是在它的 (選擇性) 初始設定式之前宣告  (如需宣告子的詳細資訊，請參閱[宣告和定義](declarations-and-definitions-cpp.md)。)  
  
 請考量以下範例：  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 如果宣告點*之後*初始化，則本機`dVar`會初始化為 7.0，全域變數的值`dVar`。 不過，由於並不是這種情況，因此 `dVar` 會初始化為未定義的值。  
  
## <a name="see-also"></a>請參閱  
 [範圍](../cpp/scope-visual-cpp.md)