---
title: 位元組索引 |Microsoft 文件
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 509e66c7ea458519eaa9dc4f52c8a6b65c789d0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863796"
---
# <a name="byte-indices"></a>位元組索引
使用下列秘訣：  
  
-   使用類索引轉換為字串顯示類似指標管理所造成的問題。 此範例中，會掃描反斜線字元的字串，請考慮：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     這可能會建立索引後隨位元組，而不是前導位元組，並因此它可能會指向`character`。  
  
-   使用[_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)解決上述問題的函式：  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     這正確索引前導位元組，因此要`character`。 `_mbclen`函式會判斷字元 （1 或 2 個位元組） 的大小。  
  
## <a name="see-also"></a>另請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [字串中的最後一個字元](../text/last-character-in-a-string.md)