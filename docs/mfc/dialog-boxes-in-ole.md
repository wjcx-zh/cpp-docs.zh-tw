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
ms.openlocfilehash: fa3d87e2cc17e297c3e6387920c6d527d8ddbe39
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767648"
---
# <a name="dialog-boxes-in-ole"></a>OLE 中的對話方塊

雖然使用者執行 OLE 功能之應用程式，但在應用程式需要從使用者的資訊以便在作業執行的時間。 MFC OLE 類別提供以收集必要的資訊的對話方塊數目。 本主題列出由 OLE 對話方塊處理的工作以及顯示這些對話方塊所需的類別。 如需 OLE 對話方塊和自訂其行為所用的結構的詳細資訊，請參閱 < [MFC 參考 》](../mfc/mfc-desktop-applications.md)。

*插入物件*<br/>
這個對話方塊中可插入複合文件，讓使用者插入新建或現有的物件。 它也可讓使用者選擇以圖示顯示項目，並可讓 [變更圖示] 命令按鈕。 顯示此對話方塊中，當使用者從 編輯 功能表中選擇 插入物件。 使用[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)類別，以顯示此對話方塊。 請注意，您無法將 MDI 應用程式插入至本身。 做為容器/伺服器的應用程式無法插入至本身，除非它是 SDI 應用程式。

*選擇性貼上*<br/>
此對話方塊可讓使用者控制將資料貼到 複合文件時使用的格式。 使用者可以選擇的資料格式、 是否要內嵌或連結的資料，以及是否要顯示為圖示。 顯示此對話方塊中，當使用者從 [編輯] 功能表選擇選擇性貼。 使用[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)類別，以顯示此對話方塊。

*變更圖示*<br/>
此對話方塊可讓使用者選取的圖示會顯示，表示連結或內嵌的項目。 顯示此對話方塊中，當使用者從 編輯 功能表中選擇 變更圖示或 選擇性貼上或轉換對話方塊中選擇 變更圖示 按鈕。 也會顯示它時使用者會開啟 [插入物件] 對話方塊中，並選擇顯示為圖示。 使用[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)類別，以顯示此對話方塊。

*Convert*<br/>
此對話方塊可讓使用者變更內嵌或連結項目的類型。 例如，如果您有內嵌在複合文件中的中繼檔，而稍後想要使用另一個應用程式來修改內嵌中繼檔，您可以使用 [轉換] 對話方塊。 這個對話方塊通常會依序按一下*項目類型*物件 [編輯] 功能表，然後在階層式功能表中，按一下轉換。 使用[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)類別，以顯示此對話方塊。 如需範例，執行 MFC OLE 範例[OCLIENT](../overview/visual-cpp-samples.md)。

*編輯連結或更新連結*<br/>
編輯連結 對話方塊可讓使用者變更連結的物件來源的相關資訊。 更新連結 對話方塊會驗證在目前的對話方塊中的所有連結項目的來源，並會顯示 編輯連結 對話方塊中，如有必要。 顯示 [編輯連結] 對話方塊中，當使用者選擇 [編輯] 功能表的連結。 第一次開啟複合文件時，通常會顯示更新連結 對話方塊。 使用任何一種[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)或[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)類別中，您要根據哪一個對話方塊中顯示。

*伺服器忙碌或伺服器沒有回應*<br/>
當使用者嘗試啟動項，而且伺服器目前無法處理要求，通常是因為伺服器正在使用另一位使用者或工作時，會顯示 [伺服器忙碌] 對話方塊。 如果伺服器不會在所有回應啟動要求，會顯示 [伺服器沒有回應] 對話方塊。 這些對話方塊會顯示透過`COleMessageFilter`根據 OLE 介面的實作， `IMessageFilter`，而且使用者可以決定是否要再次嘗試啟動要求。 使用[COleBusyDialog](../mfc/reference/colebusydialog-class.md)類別，以顯示此對話方塊。

## <a name="see-also"></a>另請參閱

[對話方塊](../mfc/dialog-boxes.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[OLE](../mfc/ole-in-mfc.md)
