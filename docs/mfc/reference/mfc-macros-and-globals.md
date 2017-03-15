---
title: "MFC 巨集和全域變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- global functions
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d26b374e233326ac5acc97486edc8d38e6bf5d81
ms.openlocfilehash: 75db28c7be1ab497ba9656136d22b114b488c4ae
ms.lasthandoff: 02/24/2017

---
# <a name="mfc-macros-and-globals"></a>MFC 巨集和全域
Mfc 程式庫可以分成兩個主要區段: （1） 的 MFC 類別和 （2） 巨集和全域資料。 如果函式或變數不是類別的成員，它可以是全域函式或變數。  
  
 MFC 程式庫和 Active Template Library (ATL) 共用字串轉換巨集。 如需詳細資訊，請參閱[字串轉換巨集](../../atl/reference/string-conversion-macros.md)ATL 文件中。  
  
 MFC 巨集和全域變數可提供以下類別的功能。  
  
## <a name="general-mfc"></a>一般 MFC  
  
-   [資料類型](../../mfc/reference/data-types-mfc.md)  
  
-   [MFC 類別物件的型別轉換](../../mfc/reference/type-casting-of-mfc-class-objects.md)  
  
-   [執行階段物件模型服務](../../mfc/reference/run-time-object-model-services.md)  
  
-   [診斷服務](../../mfc/reference/diagnostic-services.md)  
  
-   [例外狀況處理](../../mfc/reference/exception-processing.md)  
  
-   [CString 格式和訊息方塊顯示](../../mfc/reference/cstring-formatting-and-message-box-display.md)  
  
-   [訊息對應](../../mfc/reference/message-map-macros-mfc.md)  
  
-   [應用程式資訊和管理](../../mfc/reference/application-information-and-management.md)  
  
-   [標準命令和視窗 Id](../../mfc/reference/standard-command-and-window-ids.md)  
  
-   [集合類別 helper](../../mfc/reference/collection-class-helpers.md)  
  
-   [灰色和遞色點陣圖函式](../../mfc/reference/gray-and-dithered-bitmap-functions.md)  
  
-   [標準對話方塊資料交換 (DDX) 常式](../../mfc/reference/standard-dialog-data-exchange-routines.md)  
  
-   [標準對話方塊資料驗證 (DDV) 常式](../../mfc/reference/standard-dialog-data-validation-routines.md)  
  
-   [AFX 訊息](../../mfc/reference/afx-messages.md)  
  
-   [ToolBar 控制項樣式](../../mfc/reference/toolbar-control-styles.md)  
  
-   [Cmfcimagepaintarea:: Image_edit_mode 列舉](cmfcimagepaintarea-image-edit-mode-enumeration.md)  

  
## <a name="database"></a>資料庫  
  
-   [記錄欄位交換 (RFX) 函式](../../mfc/reference/record-field-exchange-functions.md)和[大量資料錄欄位交換 (bulk RFX) 函式](../../mfc/reference/record-field-exchange-functions.md)MFC ODBC 類別  
  
-   [記錄欄位交換 (DFX) 函式](../../mfc/reference/record-field-exchange-functions.md)MFC DAO 類別  
  
-   [CRecordView 和 CDaoRecordView 的對話方塊資料交換 (DDX) 函式](../../mfc/reference/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md)（MFC ODBC 和 DAO 類別）  
  
-   [OLE 控制項的對話方塊資料交換 (DDX) 函式](../../mfc/reference/dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [巨集和全域變數，以直接呼叫開放式資料庫連接 (ODBC) API 函式](../../mfc/reference/database-macros-and-globals.md)  
  
-   [DAO 資料庫引擎初始化及終止](../../mfc/reference/dao-database-engine-initialization-and-termination.md)  
  
## <a name="internet"></a>網際網路  
  
-   [網際網路 URL 剖析全域](../../mfc/reference/internet-url-parsing-globals.md)  
  
## <a name="dhtml--dhtml-event-maps"></a>DHTML / DHTML 事件對應  
  
-   [DHTML 對話方塊資料交換 (DDX) helper 巨集](../../mfc/reference/ddx-dhtml-helper-macros.md)  
  
-   [DHTML 事件對應](../../mfc/reference/dhtml-event-maps.md)  
  
## <a name="ole"></a>OLE  
  
-   [OLE 初始化](../../mfc/reference/ole-initialization.md)  
  
-   [應用程式控制](../../mfc/reference/application-control.md)  
  
-   [分派對應](../../mfc/reference/dispatch-maps.md)  
  
 此外，MFC 提供函式，呼叫[AfxEnableControlContainer](http://msdn.microsoft.com/library/7aa0b9d2-5329-4bc3-9d41-856e30fe2c2b)可讓所有 OLE 容器所都開發的完整支援的 MFC 4.0 內嵌的 OLE 控制項。  
  
## <a name="ole-controls"></a>OLE 控制項  
  
-   [變異參數類型常數](../../mfc/reference/variant-parameter-type-constants.md)  
  
-   [類型程式庫存取](../../mfc/reference/type-library-access.md)  
  
-   [屬性頁](../../mfc/reference/property-pages-mfc.md)  
  
-   [事件對應](../../mfc/reference/event-maps.md)  
  
-   [事件接收對應](../../mfc/reference/event-sink-maps.md)  
  
-   [連接對應](../../mfc/reference/connection-maps.md)  
  
-   [註冊 OLE 控制項](../../mfc/reference/registering-ole-controls.md)  
  
-   [Class factory 和授權](../../mfc/reference/class-factories-and-licensing.md)  
  
-   [OLE 控制項的持續性](../../mfc/reference/persistence-of-ole-controls.md)  
  
 本章節的第一個部分簡要討論每個先前的類別，並列出全域變數和巨集的類別，以及功能的簡短描述。 接下來是全域函式、 全域變數和 MFC 程式庫中的巨集的描述。  
  
> [!NOTE]
>  許多全域函式開頭的前置詞 「 Afx 」，但部分，例如，對話方塊資料交換 (DDX) 函式和許多資料庫函式時，不會遵循這個慣例。 做為前置詞，以 「 afx 」 開頭所有全域變數。 巨集不會啟動任何特殊的前置詞，但它們以大寫字母寫入。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../mfc/class-library-overview.md)




