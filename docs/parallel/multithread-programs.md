---
title: "多執行緒程式 |Microsoft 文件"
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
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ff73b4d3a1c8ee6971fbd3f88f491c2a5c76311
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="multithread-programs"></a>多執行緒程式
執行緒基本上是透過程式執行的路徑。 它也是 Win32 排程執行的最小單位。 執行緒堆疊時，狀態 CPU 暫存器，以及系統排程器之執行清單中的項目所組成。 每個執行緒共用處理序的所有資源。  
  
 程序包含一個或多個執行緒和程式碼、 資料和程式在記憶體中的其他資源。 一般程式資源是開啟的檔案、 信號及動態配置的記憶體。 當系統排程器可讓一個執行緒執行控制項時，就會執行程式。 排程器會判斷應該執行哪一個執行緒，以及何時應該執行。 較低優先權的執行緒必須等待較高優先權執行緒完成其工作。 在多處理器的電腦上排程器可以將個別的執行緒移至不同處理器的 CPU 負載之間取得平衡。  
  
 每個執行緒的程序中獨立運作。 除非您顯示它們彼此，個別執行和執行緒不知道處理程序中的其他執行緒。 不過，執行緒共用通用資源，必須協調工作使用號誌或另一個處理序間通訊的方法。 如需同步處理執行緒的詳細資訊，請參閱[撰寫多執行緒 Win32 程式](../parallel/writing-a-multithreaded-win32-program.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)