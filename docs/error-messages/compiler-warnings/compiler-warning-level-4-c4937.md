---
title: "編譯器警告 （層級 4） C4937 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c054051db1b7c765dd2b144b8bd3426593896a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4937"></a>編譯器警告 (層級 4) C4937
難以辨別 'text1' 和 'text2' 是否為 'directive' 的引數  
  
 因為編譯器處理指示詞引數的方式，無法辨別對編譯器有意義的名稱，例如有多種文字涵義的關鍵字 (單和雙底線格式)。  
  
 這類字串的範例包括 __cdecl 和\__forceinline。  請注意，/Za 中只會啟用雙底線格式。  
  
 下列範例會產生 C4937：  
  
```  
// C4937.cpp  
// compile with: /openmp /W4  
#include "omp.h"  
int main() {  
   #pragma omp critical ( __leave )   // C4937  
   ;  
  
   // OK  
   #pragma omp critical ( leave )  
   ;  
}  
```