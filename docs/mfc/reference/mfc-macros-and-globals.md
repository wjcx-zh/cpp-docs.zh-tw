---
title: "MFC 巨集和全域 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 71011177634e92b22cce1bc88a2ee711ad9537ed
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="mfc-macros-and-globals"></a>MFC 巨集和全域
Mfc 程式庫可以分成兩個主要區段: （1） 的 MFC 類別和 （2） 巨集和全域變數。 如果函式或變數不是類別的成員，它是全域函式或變數。  
  
 MFC 程式庫和 Active Template Library (ATL) 共用字串轉換巨集。 如需詳細資訊，請參閱[字串轉換巨集](../../atl/reference/string-conversion-macros.md)ATL 文件中。  
  
 MFC 巨集和全域變數會提供下列類別中的功能。  
  
## <a name="general-mfc"></a>一般 MFC  
  
-   [資料類型](data-types-mfc.md)  
  
-   [MFC 類別物件的型別轉型](type-casting-of-mfc-class-objects.md)  
  
-   [執行階段物件模型服務](run-time-object-model-services.md)  
  
-   [診斷服務](diagnostic-services.md)  
  
-   [例外狀況處理](exception-processing.md)  
  
-   [CString 格式和訊息方塊顯示](cstring-formatting-and-message-box-display.md)  
  
-   [訊息對應](message-map-macros-mfc.md)  

-   [委派與介面對應](delegate-and-interface-maps.md)

-   [模組和 DLL](extension-dll-macros.md)
  
-   [應用程式資訊和管理](application-information-and-management.md)  
  
-   [標準命令和視窗 Id](standard-command-and-window-ids.md)  
  
-   [集合類別 helper](collection-class-helpers.md)  
  
-   [灰色和遞色點陣圖函式](gray-and-dithered-bitmap-functions.md)  
  
-   [標準對話方塊資料交換 (DDX) 常式](standard-dialog-data-exchange-routines.md)  
  
-   [標準對話方塊資料驗證 (DDV) 常式](standard-dialog-data-validation-routines.md)  
  
-   [AFX 訊息](afx-messages.md)  
  
-   [ToolBar 控制項樣式](toolbar-control-styles.md)  
  
-   [CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉](cmfcimagepaintarea-image-edit-mode-enumeration.md)  

  
## <a name="database"></a>資料庫  
  
-   [記錄欄位交換 (RFX) 函式](record-field-exchange-functions.md)和[大量資料錄欄位交換 (bulk RFX) 函式](record-field-exchange-functions.md)MFC ODBC 類別  
  
-   [記錄欄位交換 (DFX) 函式](record-field-exchange-functions.md)MFC DAO 類別  
  
-   [CRecordView 和 CDaoRecordView 的對話方塊資料交換 (DDX) 函式](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md)（MFC ODBC 與 DAO 類別）  
  
-   [OLE 控制項的對話方塊資料交換 (DDX) 函式](dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [巨集和全域變數，以直接呼叫開放式資料庫連接 (ODBC) 應用程式開發介面函式](database-macros-and-globals.md)  
  
-   [DAO 資料庫引擎初始化及終止](dao-database-engine-initialization-and-termination.md)  
  
## <a name="internet"></a>網際網路  
  
-   [網際網路 URL 剖析全域](internet-url-parsing-globals.md)  
  
## <a name="dhtml--dhtml-event-maps"></a>DHTML / DHTML 事件對應  
  
-   [DHTML 對話方塊資料交換 (DDX) helper 巨集](ddx-dhtml-helper-macros.md)  
  
-   [DHTML 事件對應](dhtml-event-maps.md)  
  
## <a name="ole"></a>OLE  
  
-   [OLE 初始化](ole-initialization.md)  
  
-   [應用程式控制](application-control.md)  
  
-   [分派對應](dispatch-maps.md)  
  
 此外，MFC 提供函式，呼叫[AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer)啟用任何 OLE 容器開發 MFC 4.0 的完整支援內嵌 OLE 控制項。  
  
## <a name="ole-controls"></a>OLE 控制項  
  
-   [變異參數類型常數](variant-parameter-type-constants.md)  
  
-   [類型程式庫存取](type-library-access.md)  
  
-   [屬性頁](property-pages-mfc.md)  
  
-   [事件對應](event-maps.md)  
  
-   [事件接收對應](event-sink-maps.md)  
  
-   [連接對應](connection-maps.md)  
  
-   [註冊 OLE 控制項](registering-ole-controls.md)  
  
-   [Class factory 和授權](class-factories-and-licensing.md)  
  
-   [OLE 控制項的持續性](persistence-of-ole-controls.md)  
  
 本節的第一個部分簡要討論每個先前的類別，並列出全域變數和巨集的類別，以及功能的簡短描述。 接下來是全域函式、 全域變數和 MFC 程式庫中的巨集的描述。  
  
> [!NOTE]
>  許多全域函式開頭的前置詞 「 Afx 」，但部分，例如對話方塊資料交換 (DDX) 函式和許多資料庫函式不會遵循這個慣例。 做為前置詞，以 「 afx 」 開頭所有全域變數。 巨集不會啟動任何特殊的前置詞，但它們以大寫字母寫入。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../mfc/class-library-overview.md)




