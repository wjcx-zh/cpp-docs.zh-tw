---
title: 編譯器警告 （層級 1） C4129 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6405c7c156f34b49ab892304ee51a6b996ac2595
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4129"></a>編譯器警告 （層級 1） C4129
'character': 無法辨識的字元逸出序列  
  
 `character`反斜線 (\\) 中的字元或字串常數無法辨識為有效的逸出序列。 已忽略反斜線，並且不會列印。 反斜線之後的字元會列印。  
  
 若要列印單一反斜線，請指定 使用雙反斜線 (\\\\)。  
  
 C + + 標準，在 2.13.2 討論逸出序列。  
  
 下列範例會產生 C4129:  
  
```  
// C4129.cpp  
// compile with: /W1  
int main() {  
   char array1[] = "\/709";   // C4129  
   char array2[] = "\n709";   // OK  
}  
```