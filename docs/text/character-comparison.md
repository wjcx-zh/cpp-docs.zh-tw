---
title: 字元比較 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 246801abcb04cc8d9c2fd1a005183501bde240d1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612322"
---
# <a name="character-comparison"></a>字元比較
使用下列秘訣：  
  
-   比較以 ASCII 字元一個已知的前導位元組正常運作：  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   比較兩個未知的字元需要使用其中一種 Mbstring.h> 中定義的巨集：  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     這可確保會比較是否相等的雙位元組字元的兩個位元組。  
  
## <a name="see-also"></a>另請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [緩衝區溢位](../text/buffer-overflow.md)