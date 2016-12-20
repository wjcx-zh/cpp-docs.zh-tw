---
title: "MFC 巨集和全域 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Afx 命名慣例"
  - "全域函式"
  - "全域函式, MFC"
  - "全域變數, MFC"
  - "巨集"
  - "巨集, MFC"
  - "MFC, 全域函式和變數"
  - "MFC, 巨集"
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 巨集和全域
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫可以分成兩個主要元件:\(1\) MFC 類別以及 \(2\) 巨集和全域。  如果函式或變數不是類別的成員，則它是全域函式或變數。  
  
 MFC 程式庫和 Active Template Library \(ATL\) 共用字串轉換巨集。  如需詳細資訊，請參閱 ATL 文件中的[String Conversion Macros](../../atl/reference/string-conversion-macros.md)。  
  
 MFC 巨集和全域提供下列分類的功能。  
  
## 一般 MFC  
  
-   [資料型別](../../mfc/reference/data-types-mfc.md)  
  
-   [MFC 類別物件的類型轉換](../../mfc/reference/type-casting-of-mfc-class-objects.md)  
  
-   [執行階段物件模型服務](../../mfc/reference/run-time-object-model-services.md)  
  
-   [診斷服務](../../mfc/reference/diagnostic-services.md)  
  
-   [例外狀況處理](../../mfc/reference/exception-processing.md)  
  
-   [CString 格式和訊息方塊顯示](../../mfc/reference/cstring-formatting-and-message-box-display.md)  
  
-   [訊息對應](../../mfc/reference/message-map-macros-mfc.md)  
  
-   [應用程式資訊和管理](../../mfc/reference/application-information-and-management.md)  
  
-   [標準命令和視窗 ID](../../mfc/reference/standard-command-and-window-ids.md)  
  
-   [集合類別 Helper](../../mfc/reference/collection-class-helpers.md)  
  
-   [灰色和遞色點陣圖函式](../../mfc/reference/gray-and-dithered-bitmap-functions.md)  
  
-   [標準對話方塊資料交換常式 \(DDX\)](../../mfc/reference/standard-dialog-data-exchange-routines.md)  
  
-   [標準對話方塊資料驗證常式 \(DDV\)](../../mfc/reference/standard-dialog-data-validation-routines.md)  
  
-   [AFX 訊息](../../mfc/reference/afx-messages.md)  
  
-   [ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)  
  
-   [CMFCImagePaintArea::IMAGE\_EDIT\_MODE 列舉](../../mfc/reference/cmfcimagepaintarea-image-edit-mode-enumeration.md)  
  
## 資料庫  
  
-   [資料錄欄位交換 \(RFX\) 函式](../../mfc/reference/record-field-exchange-functions.md) 和 [大量資料錄欄位交換 \(大量資料錄欄位交換\) 函式](../../mfc/reference/record-field-exchange-functions.md) 的 MFC ODBC 類別  
  
-   MFC DAO 類別的[資料錄欄位交換 \(DFX\) 函式](../../mfc/reference/record-field-exchange-functions.md)  
  
-   [資料交換 \(Dialog Data Exchange，DDX 對話\) 為 CRecordView 和 CDaoRecordView 函式](../../mfc/reference/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) \(MFC ODBC 和 DAO 類別\)  
  
-   [DDX 控制項的對話方塊資料交換函式 \(OLE\)](../../mfc/reference/dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [巨集和全域對協助呼叫開放式資料庫直接連接 API 函式](../../mfc/reference/database-macros-and-globals.md)  
  
-   [DAO 資料庫引擎初始化及終止](../../mfc/reference/dao-database-engine-initialization-and-termination.md)  
  
## 網際網路  
  
-   [網際網路 URL 剖析全域](../../mfc/reference/internet-url-parsing-globals.md)  
  
## DHTML\/DHTML 事件對應  
  
-   [DHTML 對話資料交換 \(Dialog Data Exchange，DDX\) 協助程式巨集](../../mfc/reference/ddx-dhtml-helper-macros.md)  
  
-   [DHTML 事件對應](../../mfc/reference/dhtml-event-maps.md)  
  
## OLE  
  
-   [OLE 初始化](../../mfc/reference/ole-initialization.md)  
  
-   [應用程式控制](../../mfc/reference/application-control.md)  
  
-   [分派對應](../../mfc/reference/dispatch-maps.md)  
  
 此外， MFC 提供啟用所有 OLE 容器開發與 MFC 4.0 完全支援內嵌 OLE automation 控制項呼叫 [AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md) 的函式。  
  
## OLE 控制項  
  
-   [變異參數類型常數](../../mfc/reference/variant-parameter-type-constants.md)  
  
-   [類型程式庫存取](../../mfc/reference/type-library-access.md)  
  
-   [屬性頁](../../mfc/reference/property-pages-mfc.md)  
  
-   [事件對應](../../mfc/reference/event-maps.md)  
  
-   [事件接收對應](../../mfc/reference/event-sink-maps.md)  
  
-   [連接對應](../../mfc/reference/connection-maps.md)  
  
-   [註冊 OLE 控制項](../../mfc/reference/registering-ole-controls.md)  
  
-   [Class Factory 和授權](../../mfc/reference/class-factories-and-licensing.md)  
  
-   [OLE 控制項的持續性](../../mfc/reference/persistence-of-ole-controls.md)  
  
 本節中的第一個部分簡短說明每個分類並列出與描述在分類中的全域和巨集的功能。  以下是全域函式、全域變數和巨集的說明 MFC 程式庫。  
  
> [!NOTE]
>  許多全域函式以「Afx」為前置詞，但是有些對話資料交換 \(Dialog Data Exchange，DDX\) 函式和許多資料庫函式並未遵照此慣例。  所有全域變數的開頭為「afx」做為前置字元。  巨集不能以任何特殊前置詞，不過，它們以大寫字母寫入。  
  
## 請參閱  
 [類別概觀](../../mfc/class-library-overview.md)