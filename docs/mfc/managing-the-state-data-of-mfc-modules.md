---
title: 管理 MFC 模組的狀態資料
ms.date: 11/04/2016
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
ms.openlocfilehash: 757fe9d8b4c9985cd3fa36d399cdc92057c03011
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562210"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>管理 MFC 模組的狀態資料

本文討論 MFC 模組的狀態資料，以及當執行 (執行時路徑程式碼會經過應用程式) 流程進入而模組離開時，這個狀態如何更新。 同時也討論切換模組狀態與 AFX_MANAGE_STATE 和 METHOD_PROLOGUE 巨集。

> [!NOTE]
>  「模組」一詞在這裡指的是可執行的程式，或者獨立於應用程式的其他部分運作的 DLL (或一組 DLL)，不過使用的是 MFC DLL 的共用複本。 ActiveX 控制項是模組的典型例子。

如下圖所示，MFC 具有應用程式中所使用每個模組的狀態資料。 這個資料的範例包含 Windows 執行個體控制代碼 (用於載入資源)、應用程式目前 `CWinApp` 和 `CWinThread` 物件的指標、OLE 模組參考計數以及維護 Windows 物件控制代碼和相對應 MFC 物件的執行個體之間的連線的各種對應。 不過，當應用程式使用多個模組時，各個模組的狀態資料就不會涵蓋整個應用程式。 相反地，每個模組都有自己的 MFC 狀態資料私用複本。

![狀態資料的單一模組的&#40;應用程式&#41;](../mfc/media/vc387n1.gif "vc387n1")單一模組 （應用程式） 的狀態資料

模組的狀態資料是包含在結構中，並且隨時可透過指向該結構的指標取得。 如下圖所示，當執行流程進入特定模組時，模組的狀態必須是「目前的」或「有效的」。 因此，每個執行緒物件都具有指向該應用程式有效狀態結構的指標。 隨時更新此指標對於管理應用程式的全域狀態，以及維護每個模組狀態的完整性很重要。 全域狀態的管理不正確可能會導致無法預期的應用程式行為。

![狀態資料的多個模組](../mfc/media/vc387n2.gif "vc387n2")多個模組的狀態資料

換句話說，每個模組皆須負責正確地在其所有進入點的不同模組狀態間切換。 「進入點」是可供執行流程進入模組的程式碼的任何位置。 進入點包括：

- [在 DLL 中匯出的函式](../mfc/exported-dll-function-entry-points.md)

- [COM 介面的成員函式](../mfc/com-interface-entry-points.md)

- [視窗程序](../mfc/window-procedure-entry-points.md)

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)

