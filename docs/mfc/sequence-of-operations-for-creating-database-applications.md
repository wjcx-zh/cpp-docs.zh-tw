---
title: 建立資料庫應用程式的作業順序
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: c393269d6af108ee82786e9d59f81aad11428157
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372779"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>建立資料庫應用程式的作業順序

下表顯示了您在編寫資料庫應用程式時的角色和框架的作用。

> [!NOTE]
> 視覺化C++環境和精靈不支援DAO(儘管包含DAO類,您仍可以使用它們)。 Microsoft 建議您將 ODBC 用於新的 MFC 專案。 您只應在維護現有應用程式時使用 DAO。

### <a name="creating-database-applications"></a>建立資料庫應用程式

|Task|您會做|架構會做|
|----------|------------|------------------------|
|決定是使用 MFC ODBC 還是 DAO 類。|將 ODBC 用於新的 MFC 專案。 僅使用 DAO 維護現有應用程式。 有關一般資訊,請參閱文章[「數據訪問程式設計](../data/data-access-programming-mfc-atl.md)」。|框架提供支持資料庫訪問的類。|
|使用資料庫選項創建骨架應用程式。|執行 MFC 應用程式精靈。 在「資料庫支援」頁上選擇選項。 如果選擇建立記錄檢視的選項,請指定:<br /><br />- 資料來源與表格名稱或名稱<br />- 查詢名稱或名稱。|MFC 應用程式精靈建立檔並指定必要的包含。 根據指定的選項,檔可以包括記錄集類。|
|設計資料庫窗體或表單。|使用視覺化C++對話框編輯器在記錄檢視類的對話框範本資源上放置控制項。|MFC 應用程式精靈將創建一個空對話框範本資源,供您填寫。|
|根據需要創建其他記錄視圖和記錄集類。|使用類檢視創建類和對話框編輯器來設計檢視。|類視圖會為新類創建其他檔。|
|根據需要在代碼中創建記錄集物件。 使用每個紀錄集來操作記錄...|記錄集基於從[CRecordset](../mfc/reference/crecordset-class.md)派生的具有嚮導的類。|ODBC 使用記錄欄位交換 (RFX) 在資料庫和記錄集的欄位數據成員之間交換數據。 如果使用記錄檢視,則對話數據交換 (DDX) 在記錄集和記錄檢視中的控制項之間交換數據。|
|...或為要打開的每個資料庫在代碼中創建顯式[CDatabase。](../mfc/reference/cdatabase-class.md)|將記錄集對象基於資料庫物件。|資料庫物件提供數據源的介面。|
|動態地將數據列綁定到記錄集。|在 ODBC 中,將代碼添加到派生的記錄集類以管理綁定。 請參閱文章[「記錄集:動態綁定數據列 (ODBC)」。](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)||

## <a name="see-also"></a>另請參閱

[在架構上建置](../mfc/building-on-the-framework.md)<br/>
[建置 MFC 應用程式的作業順序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[建立 OLE 應用程式的作業順序](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[建立 ActiveX 控制項的作業順序](../mfc/sequence-of-operations-for-creating-activex-controls.md)
