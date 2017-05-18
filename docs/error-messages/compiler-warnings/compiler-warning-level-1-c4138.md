---
title: "編譯器警告 （層級 1） C4138 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 3f3009b5a4d8fd7c3810b8039e04f99c7eb9d6cc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4138"></a>編譯器警告 (層級 1) C4138
在註解外部找到 '*/'  
  
 結案註解分隔符號必須在開啟註解分隔符號之後。 編譯器會假設星號 (**\***) 和正斜線 (/) 之間有個空格。  
  
## <a name="example"></a>範例  
  
```  
// C4138a.cpp  
// compile with: /W1  
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning  
int main()  
{  
}  
```  
  
 此警告可能因嘗試巢狀化註解所致。  
  
 如果您將包含註解的程式碼區段註解化，再將程式碼括在 **#if / #endif** 區塊中，並將控制運算式設定為零，應可解決此警告：  
  
```  
// C4138b.cpp  
// compile with: /W1  
#if 0  
int my_variable;   /* Declaration currently not needed */  
#endif  
int main()  
{  
}  
```
