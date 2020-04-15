---
title: MFC 巨集和全域
ms.date: 11/04/2016
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
ms.openlocfilehash: ed45fc7014bda18887be6dc8fbcdff8ba9a9c5f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373048"
---
# <a name="mfc-macros-and-globals"></a>MFC 巨集和全域

Microsoft 基礎類庫可以分為兩個主要部分:(1) MFC 類和 (2) 宏和全域。 如果函數或變數不是類的成員,則它是全域函數或變數。

MFC 庫和活動範本庫 (ATL) 共用字串轉換巨集。 有關詳細資訊,請參閱 ATL 文件中的[字串轉換巨集](../../atl/reference/string-conversion-macros.md)。

MFC 宏和全域提供以下類別的功能。

## <a name="general-mfc"></a>一般MFC

- [資料類型](data-types-mfc.md)

- [MFC 類別類型轉換](type-casting-of-mfc-class-objects.md)

- [執行時物件模型服務](run-time-object-model-services.md)

- [診斷服務](diagnostic-services.md)

- [例外處理](exception-processing.md)

- [CString 格式與訊息盒顯示](cstring-formatting-and-message-box-display.md)

- [訊息對應](message-map-macros-mfc.md)

- [委託和介面對應](delegate-and-interface-maps.md)

- [模組和 DLL](extension-dll-macros.md)

- [套用資訊與管理](application-information-and-management.md)

- [標準命令與視窗指示](standard-command-and-window-ids.md)

- [集合類說明器](collection-class-helpers.md)

- [灰色與抖除點陣陣陣](gray-and-dithered-bitmap-functions.md)

- [標準對話框資料交換 (DDX) 例程](standard-dialog-data-exchange-routines.md)

- [標準對話框資料驗證 (DDV) 例程](standard-dialog-data-validation-routines.md)

- [AFX 訊息](afx-messages.md)

- [ToolBar 控制項樣式](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>資料庫

- MFC ODBC 類別[的記錄現場交換 (RFX) 功能](record-field-exchange-functions.md)和[大量記錄現場交換 (批量 RFX) 功能](record-field-exchange-functions.md)

- MFC DAO 類別[的記錄欄位交換 (DFX) 函數](record-field-exchange-functions.md)

- CRecordView 和 CDaoRecordView(MFC ODBC 和 DAO 類別[)的對話資料交換 (DDX) 功能](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md)

- [用於 OLE 控制的交談 (DDX) 函數](dialog-data-exchange-functions-for-ole-controls.md)

- [巨集和全域,以協助直接呼叫開放資料庫連線 (ODBC) API 功能](database-macros-and-globals.md)

- [DAO 資料庫引擎初始化與終止](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [網際網路網址解析全域](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML / DHTML 事件對應

- [DHTML 對話框資料交換 (DDX) 說明器巨集](ddx-dhtml-helper-macros.md)

- [DHTML 事件對應](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [OLE 初始化](ole-initialization.md)

- [應用程式控制](application-control.md)

- [調度地圖](dispatch-maps.md)

此外,MFC 還提供名為[AfxEnableControl 容器](ole-initialization.md#afxenablecontrolcontainer)的功能,使使用 MFC 4.0 開發的任何 OLE 容器能夠完全支援嵌入式 OLE 控制。

## <a name="ole-controls"></a>OLE 控制

- [變數參數類型常量](variant-parameter-type-constants.md)

- [型態庫存取](type-library-access.md)

- [「屬性頁」](property-pages-mfc.md)

- [事件地圖](event-maps.md)

- [事件接收器對應](event-sink-maps.md)

- [連接對應](connection-maps.md)

- [註冊 OLE 控制項](registering-ole-controls.md)

- [級工廠和授權](class-factories-and-licensing.md)

- [OLE 控制項的持久性](persistence-of-ole-controls.md)

本節的第一部分簡要討論了前面的每個類別,並列出了類別中的全域和宏,以及功能的簡要說明。 以下是 MFC 庫中全域函數、全域變數和宏的說明。

> [!NOTE]
> 許多全域函數以前綴"Afx"開頭,但有些,例如,對話框數據交換 (DDX) 函數和許多資料庫函數,不遵循此約定。 所有全域變數都以「afx」作為首碼開頭。 宏不以任何特定首碼開頭,但它們用大寫字母編寫。

## <a name="see-also"></a>另請參閱

[類別概觀](../../mfc/class-library-overview.md)
