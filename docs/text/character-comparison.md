---
title: "字元比較 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28c2cd3a2e868a595d73d06b5cae8e71ec8cc313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="character-comparison"></a>字元比較
使用下列秘訣：  
  
-   比較以 ASCII 字元的已知的前導位元組正常運作：  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   比較兩個未知的字元需要使用其中一種 Mbstring.h 中定義的巨集：  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     這可確保會比較是否相等的雙位元組字元的兩個位元組。  
  
## <a name="see-also"></a>請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [緩衝區溢位](../text/buffer-overflow.md)