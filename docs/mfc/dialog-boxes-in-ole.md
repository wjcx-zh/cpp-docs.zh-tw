---
title: 在 OLE 中的對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe7f9b4b97fd17e73c3dd9f113a87d8f087b93c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929659"
---
# <a name="dialog-boxes-in-ole"></a>OLE 中的對話方塊
當使用者執行 OLE 功能之應用程式時，但有些的時候應用程式時需要使用者的資訊才能執行作業。 MFC OLE 類別提供對話方塊，以收集必要的資訊的數的字。 本主題列出由 OLE 對話方塊處理的工作和顯示這些對話方塊所需的類別。 如需 OLE 對話方塊，以及用來自訂其行為的結構的詳細資訊，請參閱[MFC 參考](../mfc/mfc-desktop-applications.md)。  
  
 *插入物件*  
 此對話方塊可讓使用者插入新建立的或現有的物件插入複合文件中。 它也可讓使用者選擇要以圖示顯示項目，並啟用 [變更圖示] 命令按鈕。 顯示此對話方塊中，當使用者選擇 編輯 功能表的 插入物件。 使用[COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)類別來顯示此對話方塊。 請注意，您無法將 MDI 應用程式插入至本身。 做為容器/伺服器的應用程式無法插入至本身，除非它是 SDI 應用程式。  
  
 *選擇性貼上*  
 這個對話方塊可讓使用者控制將資料貼入複合文件時使用的格式。 使用者可以選擇資料的格式、 是否要內嵌或連結資料，以及是否要顯示為圖示。 當使用者選擇選擇性貼上從 [編輯] 功能表顯示這個對話方塊。 使用[COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)類別來顯示此對話方塊。  
  
 *變更圖示*  
 這個對話方塊可讓使用者選取的圖示隨即出現，表示連結或內嵌的項目。 顯示此對話方塊中，使用者就可以從 編輯 功能表選擇 變更圖示或 選擇性貼上或轉換的對話方塊中選擇 變更圖示 按鈕時。 也會顯示它時使用者會開啟 [插入物件] 對話方塊，並選擇顯示為圖示。 使用[COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)類別來顯示此對話方塊。  
  
 *轉換*  
 這個對話方塊可讓使用者變更內嵌或連結項目的類型。 比方說，如果您有複合文件中內嵌中繼檔，而稍後想要使用另一個應用程式來修改內嵌中繼檔，您可以使用 [轉換] 對話方塊。 這個對話方塊通常會依序按一下*項目類型*物件的階層式功能表上，編輯 功能表，然後按一下 轉換。 使用[COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)類別來顯示此對話方塊。 如需範例，請執行 MFC OLE 範例[OCLIENT](../visual-cpp-samples.md)。  
  
 *編輯連結或更新連結*  
 編輯連結 對話方塊可讓使用者變更連結物件的來源的相關資訊。 更新連結 對話方塊會驗證目前的對話方塊中的所有連結項目的來源，並顯示 編輯連結 對話方塊，如有必要。 當使用者選擇 [編輯] 功能表的連結會顯示 [編輯連結] 對話方塊。 複合文件第一次開啟時，通常會顯示更新的連結 對話方塊。 使用[COleLinksDialog](../mfc/reference/colelinksdialog-class.md)或[COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)類別中，您要根據的對話方塊中顯示。  
  
 *伺服器忙碌或伺服器沒有回應*  
 當使用者嘗試啟動項，而且伺服器目前無法處理要求時，通常是因為伺服器正在使用另一位使用者或工作時，會顯示 [伺服器忙碌] 對話方塊。 如果伺服器不會完全回應啟動要求，會顯示 [伺服器沒有回應] 對話方塊。 這些對話方塊會顯示透過`COleMessageFilter`根據 OLE 介面的實作， `IMessageFilter`，而且使用者可以決定是否要再次嘗試啟動要求。 使用[COleBusyDialog](../mfc/reference/colebusydialog-class.md)類別來顯示此對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)

