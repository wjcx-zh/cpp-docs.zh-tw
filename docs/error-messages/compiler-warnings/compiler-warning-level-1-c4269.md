---
title: 編譯器警告 （層級 1） C4269 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e393c657e12f84d3cadfacd469e35e3472a39d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281787"
---
# <a name="compiler-warning-level-1-c4269"></a>編譯器警告 (層級 1) C4269
'identifier': 'const' 的自動資料初始化編譯器產生預設建構函式會產生不可靠的結果  
  
 A **const**編譯器產生預設建構函式以初始化自動非一般的類別執行個體。  
  
## <a name="example"></a>範例  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 由於類別的這個執行個體在堆疊的初始值來產生`m_data`可以是任何項目。 此外，因為它是**const**執行個體的值`m_data`永遠不會變更。