---
title: "OLE 中的對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "對話方塊"
  - "對話方塊, 關於對話方塊"
  - "對話方塊, OLE"
  - "插入物件"
  - "MFC 對話方塊, OLE 對話方塊"
  - "OLE 對話方塊"
  - "OLE 對話方塊, 關於 OLE 對話方塊"
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 中的對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者執行 OLE 允許應用程式時，有時當應用程式需要使用者的資訊才能執行作業時。  MFC OLE 類別提供一些對話方塊收集所需要的資訊。  本主題列出 OLE 對話方塊處理的工作和必要的類別來顯示這些對話方塊。  如需 OLE 用於對話方塊和結構的細節自訂其行為，請參閱 [MFC 參考](../mfc/mfc-desktop-applications.md)。  
  
 *插入物件*  
 這個對話方塊可讓使用者插入新建立或現有物件的複合文件。  它也可讓使用者選取的項目顯示為圖示並啟用變更圖示命令按鈕。  當使用者在編輯\] 功能表中，選擇插入物件中顯示這個對話方塊。  使用 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md) 類別來顯示這個對話方塊。  請注意您無法插入 MDI 應用程式至本身。  為容器\/伺服器的應用程式不能插入至本身，除非它是 SDI 應用程式。  
  
 *選擇性貼上*  
 當貼上資料輸入複合文件時，這個對話方塊可讓使用者控制項所使用的格式。  使用者是否可以選取資料的格式，內嵌或連結資料並將其顯示為圖示。  當使用者從編輯功能表選擇貼上時，顯示這個對話方塊。  使用 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md) 類別來顯示這個對話方塊。  
  
 *圖示變更*  
 這個對話方塊可讓使用者選取的圖示會顯示代表連結或內嵌項目。  當使用者在編輯功能表選擇變更圖示或選取特殊中貼上的變更圖示按鈕或轉換對話方塊時，顯示這個對話方塊。  此外，當使用者開啟插入物件對話方塊並選取顯示為圖示時，顯示它。  使用 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md) 類別來顯示這個對話方塊。  
  
 *轉換*  
 這個對話方塊可讓使用者變更內嵌或連結的項目類型。  例如，如果您在複合檔案內嵌在組件中的中繼檔和之後要使用另一個應用程式修改內嵌中繼檔，您可以使用轉換對話方塊。  這個對話方塊中按一下 *項目類型* 物件通常會顯示在編輯功能表，然後在串聯功能表，按一下轉換。  使用 [COleInsertDialog](../mfc/reference/coleconvertdialog-class.md) 類別來顯示這個對話方塊。  如需範例，請執行 MFC OLE [OCLIENT](../top/visual-cpp-samples.md)範例。  
  
 *編輯連結或更新連結。*  
 編輯連結對話方塊可讓使用者變更有關已連結物件來源的相關資訊。  更新連結對話方塊確認所有連結項目來源目前對話方塊中的值，並在必要時顯示編輯連結對話方塊。  當使用者從編輯功能表選取連結時，顯示編輯連結對話方塊。  當第一次開啟時，更新連結對話方塊通常會顯示複合文件。  使用 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md) 或 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md) 類別以依據要顯示的對話方塊。  
  
 *伺服器忙碌或伺服器沒有回應*  
 當使用者嘗試啟動項目時，伺服器忙碌對話方塊通常會顯示，不過因為伺服器已被其他使用者或工作正在使用中，所以伺服器目前無法處理要求。  如果伺服器根本不會回應，啟動要求沒有回應的伺服器對話方塊隨即顯示。  這些對話方塊來顯示 `COleMessageFilter`，根據 OLE 介面 **IMessageFilter**的實作，因此，使用者可以決定是否要嘗試啟動再次要求。  使用 [COleBusyDialog](../mfc/reference/colebusydialog-class.md) 類別來顯示這個對話方塊。  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [OLE](../mfc/ole-in-mfc.md)