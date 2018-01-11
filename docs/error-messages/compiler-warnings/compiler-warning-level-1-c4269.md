---
title: "編譯器警告 （層級 1） C4269 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4269
dev_langs: C++
helpviewer_keywords: C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e3d276aa5744d457ee987334d65728b1835593ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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