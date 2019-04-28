---
title: 建立資料庫應用程式的作業順序
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: efd6b12b186ce0ef1c0caf57f313f6aa50425fec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308494"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>建立資料庫應用程式的作業順序

下表顯示您的角色和架構的角色中撰寫資料庫應用程式。

> [!NOTE]
>  視覺效果C++環境和精靈不支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 建議您針對新的 MFC 專案，使用 ODBC。 您只應該使用 DAO，在維護現有的應用程式。

### <a name="creating-database-applications"></a>建立資料庫應用程式

|工作|您會做|架構會做|
|----------|------------|------------------------|
|決定是否要使用 MFC ODBC 或 DAO 類別。|針對新的 MFC 專案中使用 ODBC。 您可以使用 DAO 來維護現有的應用程式。 如需一般資訊，請參閱文章[資料存取程式設計](../data/data-access-programming-mfc-atl.md)。|架構會提供類別，可支援資料庫存取權。|
|建立基本架構應用程式與資料庫選項。|執行 MFC 應用程式精靈。 選取資料庫支援頁面上的選項。 如果您選擇一個選項可建立資料錄檢視時，也指定：<br /><br />資料來源和資料表名稱或名稱<br />-查詢名稱。|MFC 應用程式精靈會建立檔案，並指定包含必要的。 根據您指定的選項，檔案可以包含資料錄集類別。|
|設計您的資料庫表單。|使用視覺效果C++對話方塊編輯器，將控制項放入您的資料錄檢視類別的對話方塊範本資源。|MFC 應用程式精靈會建立為您填入的空白對話方塊範本資源。|
|視需要建立額外的資料錄檢視和資料錄集類別。|您可以使用 類別檢視來建立類別和對話方塊編輯器設計檢視。|類別檢視 中建立額外的檔案，為您的新類別。|
|視您的程式碼，請建立資料錄集物件。 您可以使用每個資料錄集來操作記錄...|資料錄集根據衍生自類別[CRecordset](../mfc/reference/crecordset-class.md)精靈。|ODBC 會使用資料錄欄位交換 (RFX)，資料庫和資料錄集的欄位資料成員之間交換資料。 如果您使用資料錄檢視時，對話方塊資料交換 (DDX) 之間交換資料的資料錄集和資料錄檢視上的控制項。|
|...或建立明確[CDatabase](../mfc/reference/cdatabase-class.md)在您的程式碼，為您想要開啟每個資料庫中。|資料錄集物件為基礎的資料庫物件。|資料庫物件提供資料來源的介面。|
|將繫結資料行資料錄集動態。|在 ODBC 中，加入您的衍生的資料錄集類別，來管理繫結中的程式碼。 請參閱文章[資料錄集：動態繫結資料行 (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||

## <a name="see-also"></a>另請參閱

[在架構上建置](../mfc/building-on-the-framework.md)<br/>
[建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)
