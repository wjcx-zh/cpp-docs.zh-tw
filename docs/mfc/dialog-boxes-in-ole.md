---
title: OLE 中的對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
ms.openlocfilehash: 997bfc0bda05f5a2520c102cb38777b533bcef95
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685785"
---
# <a name="dialog-boxes-in-ole"></a>OLE 中的對話方塊

當使用者執行具備 OLE 功能的應用程式時，有時候應用程式會需要使用者的資訊才能執行作業。 MFC OLE 類別提供數個對話方塊來收集所需的資訊。 本主題列出 OLE 對話方塊所處理的工作，以及顯示這些對話方塊所需的類別。 如需 OLE 對話方塊和用來自訂其行為之結構的詳細資訊，請參閱[MFC 參考](../mfc/mfc-desktop-applications.md)。

*插入物件*<br/>
這個對話方塊可讓使用者將新建立或現有的物件插入複合檔案中。 它也可讓使用者選擇將專案顯示為圖示，並啟用 [變更圖示] 命令按鈕。 當使用者從 [編輯] 功能表選擇 [插入物件] 時，顯示此對話方塊。 使用[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)類別來顯示此對話方塊。 請注意，您無法將 MDI 應用程式插入至本身。 做為容器/伺服器的應用程式無法插入至本身，除非它是 SDI 應用程式。

*貼上特殊的*<br/>
這個對話方塊可讓使用者控制將資料貼入複合檔案時所使用的格式。 使用者可以選擇資料的格式、是否要內嵌或連結資料，以及是否要將它顯示為圖示。 當使用者從 [編輯] 功能表選擇 [貼上特殊] 時，顯示此對話方塊。 使用[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)類別來顯示此對話方塊。

*變更圖示*<br/>
這個對話方塊可讓使用者選取要顯示的圖示，以代表連結或內嵌專案。 當使用者從 [編輯] 功能表選擇變更圖示，或選擇 [貼上特殊] 或 [轉換] 對話方塊中的 [變更圖示] 按鈕時，就會顯示此對話方塊。 當使用者開啟 [插入物件] 對話方塊，並選擇 [顯示為圖示] 時，也會顯示它。 使用[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)類別來顯示此對話方塊。

*Convert*<br/>
這個對話方塊可讓使用者變更內嵌或連結專案的類型。 例如，如果您已在複合檔案中內嵌中繼檔，而稍後想要使用另一個應用程式來修改內嵌的中繼檔，則可以使用 [轉換] 對話方塊。 在 [編輯] 功能表上按一下 [*專案類型*] [物件]，然後在串聯功能表上按一下 [轉換]，通常會顯示此對話方塊。 使用[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)類別來顯示此對話方塊。 如需範例，請執行 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)。

*編輯連結或更新連結*<br/>
[編輯連結] 對話方塊可讓使用者變更連結化物件之來源的相關資訊。 [更新連結] 對話方塊會驗證目前對話方塊中所有連結專案的來源，並在必要時顯示 [編輯連結] 對話方塊。 當使用者從 [編輯] 功能表選擇連結時，顯示 [編輯連結] 對話方塊。 第一次開啟複合檔案時，通常會顯示 [更新連結] 對話方塊。 請根據您要顯示的對話方塊，使用[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)或[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)類別。

*伺服器忙碌或伺服器沒有回應*<br/>
當使用者嘗試啟動專案，而伺服器目前無法處理要求時，通常是因為其他使用者或工作正在使用伺服器，就會顯示 [伺服器忙碌中] 對話方塊。 如果伺服器沒有回應啟動要求，則會顯示 [伺服器沒有回應] 對話方塊。 這些對話方塊會根據 OLE 介面 `IMessageFilter` 的執行，透過 `COleMessageFilter` 顯示，而使用者可以決定是否要再次嘗試啟用要求。 使用[COleBusyDialog](../mfc/reference/colebusydialog-class.md)類別來顯示此對話方塊。

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
