---
title: "遞增和遞減指標 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e9eccf65f091c8c5c273f6a65cb7e81b0d386afa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="incrementing-and-decrementing-pointers"></a>增量和遞減指標
使用下列秘訣：  
  
-   指向前導位元組，而非後隨位元組。 它通常是不安全的後隨位元組指標。 它通常會安全掃描轉寄而非以反向方向的字串。  
  
-   指標遞增/遞減函式和巨集可在整個字元上移動時，有：  
  
    ```  
    sz1++;  
    ```  
  
     會變成：  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc`和`_mbsdec`函式正確遞增和遞減中`character`單位，而不管字元大小。  
  
-   遞減，您需要的標頭的字串，如下所示的指標：  
  
    ```  
    sz2--;  
    ```  
  
     會變成：  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     或者，您的標頭指標可以指向有效的字元在字串中，以便：  
  
    ```  
    sz2Head < sz2  
    ```  
  
     您必須有一個已知有效的前導位元組的指標。  
  
-   您可能想要維護的更快速呼叫前一個字元的指標`_mbsdec`。  
  
## <a name="see-also"></a>請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)   
 [位元組索引](../text/byte-indices.md)