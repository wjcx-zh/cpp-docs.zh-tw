---
title: "編譯器錯誤 C3163 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3163
dev_langs:
- C++
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3cbb5c5c3e8391b3a549fc0c34661dc86b492c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3163"></a>編譯器錯誤 C3163
'construct': 屬性與上一個宣告不一致  
  
 套用至定義的屬性會與套用至宣告之屬性衝突。  
  
 若要解決 C3163 的方法之一是以消除向前宣告上的屬性。 向前宣告上的屬性應該能早於在定義上的屬性或者，最多會等於給它們。  
  
 C3163 錯誤的可能原因包括 Microsoft 原始程式碼註釋語言 (SAL)。 除非您使用編譯您的專案，否則 SAL 巨集不要展開**/ 分析**旗標。 /Analyze 沒有順利進行編譯的程式可能會擲回 C3163，如果您嘗試重新編譯時與 / 分析選項。 如需 SAL 的詳細資訊，請參閱[SAL 註釋](../../c-runtime-library/sal-annotations.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3163。  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## <a name="see-also"></a>請參閱  
 [SAL 註釋](../../c-runtime-library/sal-annotations.md)