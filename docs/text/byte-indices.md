---
title: 位元組索引 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5beb69ef7d9d3356eddef40c6bce6483079d934a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590796"
---
# <a name="byte-indices"></a>位元組索引
使用下列秘訣：  
  
-   使用位元組類索引轉換為字串提供類似於指標操作所造成的問題。 請考慮此範例中，它會掃描反斜線字元的字串：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     這可能會編製索引後隨位元組，而不是前導位元組，並因此它可能會指向`character`。  
  
-   使用[_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)解決上述問題的函式：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     這正確索引前導位元組，因此要`character`。 `_mbclen`函式會判斷字元 （1 或 2 個位元組） 的大小。  
  
## <a name="see-also"></a>另請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [字串中的最後一個字元](../text/last-character-in-a-string.md)