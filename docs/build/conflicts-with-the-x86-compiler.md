---
title: "衝突與 x86 編譯器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b2b9c4cf871e8436a8da34a862d205541e7dc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="conflicts-with-the-x86-compiler"></a>與 x86 編譯器衝突
資料類型都大於 4 個位元組會不自動對齊堆疊上使用 x86 編譯器進行編譯的應用程式。 因為編譯器會是 4 位元組對齊的堆疊、 大於 4 個位元組，比方說，64 位元整數的任何項目無法自動對齊 8 位元組位址的 x86 架構。  
  
 處理未對齊的資料有兩個含意。  
  
-   可能需要較長的時間比所需存取對齊的位置存取未對齊的位置。  
  
-   未配置的位置不能在連鎖的作業。  
  
 如果您需要多個嚴格的對齊方式，使用`__declspec(align(N)) on your variable declarations`。 這會導致編譯器以動態方式對齊堆疊，以符合您的規格。 不過，動態調整堆疊在執行階段可能會導致應用程式的執行速度緩慢。  
  
## <a name="see-also"></a>請參閱  
 [類型和儲存區](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)