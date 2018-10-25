---
title: MFC 巨集和全域 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4833c10772afd7cfd167171821e13a000a611f15
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083031"
---
# <a name="mfc-macros-and-globals"></a>MFC 巨集和全域

Microsoft Foundation 類別程式庫可以分成兩個主要區段: （1） 的 MFC 類別和 （2） 巨集和全域變數。 如果函式或變數不是類別的成員，它是全域函式或變數。

MFC 程式庫和 Active Template Library (ATL) 共用字串轉換巨集。 如需詳細資訊，請參閱 <<c0> [ 字串轉換巨集](../../atl/reference/string-conversion-macros.md)ATL 文件中。

MFC 巨集和全域變數提供以下類別的功能。

## <a name="general-mfc"></a>一般 MFC

- [資料類型](data-types-mfc.md)

- [MFC 類別物件的型別轉換](type-casting-of-mfc-class-objects.md)

- [執行階段物件模型服務](run-time-object-model-services.md)

- [診斷服務](diagnostic-services.md)

- [例外狀況處理](exception-processing.md)

- [CString 格式和訊息方塊顯示](cstring-formatting-and-message-box-display.md)

- [訊息對應](message-map-macros-mfc.md)

- [委派和介面對應](delegate-and-interface-maps.md)

- [模組和 DLL](extension-dll-macros.md)

- [應用程式資訊和管理](application-information-and-management.md)

- [標準命令和視窗 Id](standard-command-and-window-ids.md)

- [集合類別 helper](collection-class-helpers.md)

- [灰色和遞色點陣圖函式](gray-and-dithered-bitmap-functions.md)

- [標準對話方塊資料交換 (DDX) 常式](standard-dialog-data-exchange-routines.md)

- [標準對話方塊資料驗證 (DDV) 常式](standard-dialog-data-validation-routines.md)

- [AFX 訊息](afx-messages.md)

- [ToolBar 控制項樣式](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>資料庫

- [記錄欄位交換 (RFX) 函數](record-field-exchange-functions.md)並[大量資料錄欄位交換 (bulk RFX) 函式](record-field-exchange-functions.md)MFC ODBC 類別

- [記錄欄位交換 (DFX) 函式](record-field-exchange-functions.md)MFC DAO 類別

- [CRecordView 和 CDaoRecordView 的對話方塊資料交換 (DDX) 函式](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md)（MFC ODBC 和 DAO 類別）

- [OLE 控制項的對話方塊資料交換 (DDX) 函式](dialog-data-exchange-functions-for-ole-controls.md)

- [巨集和全域變數，以協助直接呼叫開放式資料庫連接 (ODBC) API 函式](database-macros-and-globals.md)

- [DAO 資料庫引擎初始化及終止](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>網際網路

- [網際網路 URL 剖析全域](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML / DHTML 事件對應

- [DHTML 對話方塊資料交換 (DDX) 協助程式巨集](ddx-dhtml-helper-macros.md)

- [DHTML 事件對應](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [OLE 初始化](ole-initialization.md)

- [應用程式控制](application-control.md)

- [分派對應](dispatch-maps.md)

此外，MFC 提供函式，呼叫[AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer)任何 OLE 容器開發的完整支援的 MFC 4.0 可讓內嵌 OLE 控制項。

## <a name="ole-controls"></a>OLE 控制項

- [變異參數類型常數](variant-parameter-type-constants.md)

- [類型程式庫存取](type-library-access.md)

- [屬性頁](property-pages-mfc.md)

- [事件對應](event-maps.md)

- [事件接收對應](event-sink-maps.md)

- [連接對應](connection-maps.md)

- [註冊 OLE 控制項](registering-ole-controls.md)

- [Class factory 和授權](class-factories-and-licensing.md)

- [OLE 控制項的持續性](persistence-of-ole-controls.md)

本章節的第一個部分簡要討論每個先前的類別，並列出的全域變數和巨集，在類別中，以及功能的簡短描述。 接下來是全域函式、 全域變數和 MFC 程式庫中的巨集的描述。

> [!NOTE]
>  許多全域函式開頭的前置詞 「 Afx 」，但某些，比方說，對話方塊資料交換 (DDX) 函式和許多資料庫函式，不會遵循此慣例。 所有全域變數的開頭 「 afx 」 做為前置詞。 不要啟動巨集，這是以任何特定的前置詞，但它們以大寫字母撰寫。

## <a name="see-also"></a>另請參閱

[類別概觀](../../mfc/class-library-overview.md)

