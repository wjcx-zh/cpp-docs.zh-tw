---
title: "OLE 通用對話方塊類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 類別 [C++]"
  - "通用對話方塊類別"
  - "對話方塊類別 [C++], OLE"
  - "OLE 通用對話方塊類別 [C++]"
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 通用對話方塊類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別會藉由實作一些標準 OLE 對話方塊處理一般 OLE 工作。  它們為 OLE 功能也提供一致的使用者介面。  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 由框架包含所有 OLE 對話方塊的通用實作。  在使用者介面 \(UI\) 分類的所有對話方塊類別中衍生自這個基底類別。  `COleDialog`不可以直接使用。  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 顯示插入物件對話方塊，插入新的 OLE 連結或內嵌項目使用標準的使用者介面。  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 顯示選擇性貼上對話方塊，實作的編輯選擇性貼上命令使用標準的使用者介面。  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 顯示編輯連結對話方塊中，使用標準的使用者介面對連結項目的修改資訊。  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 顯示變更圖示對話方塊，變更的圖示使用標準的使用者介面與 OLE 內嵌或連結的項目。  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 顯示轉換對話方塊，轉譯的 OLE 項目標準使用者介面從一個型別對應到另一個。  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 封裝 Windows 的通用OLE屬性的對話方塊。  通用 OLE 屬性對話方塊讓您能夠輕鬆顯示和修改 OLE 文件項目的某些屬性與 Windows 標準。  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 顯示更新對話方塊中，更新的所有連結使用標準的使用者介面在文件。  對話方塊包含進度指示器指出關閉更新程序是如何對完成。  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 顯示變更來源對話方塊中，變更連結的來源或目的使用標準的使用者介面。  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 顯示伺服器沒有回應的處理和的伺服器對話方塊，處理呼叫標準使用者介面為忙碌應用程式。  通常會自動顯示由 `COleMessageFilter` 實作。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)