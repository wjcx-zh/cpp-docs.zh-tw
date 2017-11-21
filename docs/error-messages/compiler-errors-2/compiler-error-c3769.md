---
title: "編譯器錯誤 C3769 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3769
dev_langs: C++
helpviewer_keywords: C3769
ms.assetid: 341675e1-7428-4da6-8275-1b2f0a70dacc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 097b12ca4cdca8f465fd5383e42609187b66d32e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3769"></a>編譯器錯誤 C3769
'type': 巢狀的類別不能有相同的名稱為立即封入類別  
  
 巢狀的類別不能直接封入類別名稱相同。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3769。  
  
```  
// C3769.cpp  
// compile with: /c  
class x {  
   class x {};   // C3769  
   class y {  
      class x{};   // OK  
   };  
};  
```