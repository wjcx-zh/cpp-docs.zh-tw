---
title: C + + 中宣告點 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e42f43e6187e19df6e9c1111c0e92aa4b9929199
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>另請參閱  
 [範圍](../cpp/scope-visual-cpp.md)