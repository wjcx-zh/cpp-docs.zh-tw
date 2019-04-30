---
title: 多執行緒程式
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
ms.openlocfilehash: fd10893ecd33d39b531b9451dec708ea31c121d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407818"
---
# <a name="multithread-programs"></a>多執行緒程式

執行緒基本上是執行的透過程式路徑。 它也是 Win32 排程執行的最小單位。 執行緒堆疊，以及 CPU 暫存器中，系統排程器的 [執行] 清單中的項目狀態所組成。 每個執行緒共用處理序的所有資源。

處理程序是由一個或多個執行緒和程式碼、 資料和程式在記憶體中的其他資源所組成。 一般程式資源是開啟的檔案、 信號及動態配置的記憶體。 當系統排程器可讓一個執行緒執行控制時，就會執行程式。 排程器會判斷應該執行哪一個執行緒，以及何時應該執行。 較低優先權的執行緒，可能必須等待較高優先順序的執行緒完成其工作。 在多處理器電腦上排程器可以將個別的執行緒移至不同的處理器的 CPU 負載之間取得平衡。

每個執行緒的處理序中獨立運作。 除非您讓它們可以看到彼此，個別執行的執行緒，而且不知道處理程序中的其他執行緒。 不過，共用通用的資源的執行緒必須協調其工作使用號誌或另一個處理序間通訊的方法。 如需有關同步處理執行緒的詳細資訊，請參閱 <<c0> [ 撰寫多執行緒 Win32 程式](writing-a-multithreaded-win32-program.md)。

## <a name="see-also"></a>另請參閱

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)
