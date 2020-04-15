---
title: MFC：使用具有文件和檢視的資料庫類別
ms.date: 11/04/2016
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
ms.openlocfilehash: 9e071e0cc25492073cd74ed517284476b6e49ef8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368893"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC：使用具有文件和檢視的資料庫類別

您可以使用具有或不帶文件/檢視體系結構的 MFC 資料庫類。 本主題強調使用文檔和檢視。 它解釋了:

- 如何使用`CRecordView`物件作為文件的主檢視[編寫基於窗體的應用程式](#_core_writing_a_form.2d.based_application)。

- [如何在文件與檢視中使用紀錄集物件](#_core_using_recordsets_in_documents_and_views)。

- [其他注意事項](#_core_other_factors)。

有關備選方案,請參閱[MFC:使用沒有文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>編寫基於表單的應用程式

許多數據訪問應用程式都基於表單。 使用者介面是一個表單,其中包含使用者檢查、輸入或編輯數據的控制項。 要讓應用程式表單以使用類別`CRecordView`。 當您執行 MFC 應用程式精靈並在**資料庫支援**頁上選擇**ODBC**用戶端類型`CRecordView`時,專案將用於檢視類。

在基於表單的應用程式中,每個記錄檢視物件都存儲指向物件的`CRecordset`指標。 框架的記錄欄位交換 (RFX) 機制在記錄集和數據源之間交換數據。 對話框資料交換 (DDX) 機制在記錄集物件的欄位數據成員和窗體上的控制項之間交換資料。 `CRecordView`還提供預設命令處理程式函數,用於在窗體上從記錄導航到記錄。

要使用應用程式精靈建立以表單的應用程式,請參考[建立您的系統的 MFC 應用程式](../mfc/reference/creating-a-forms-based-mfc-application.md)與[資料庫支援,MFC 應用程式精靈](../mfc/reference/database-support-mfc-application-wizard.md)。

關於表單的完整討論,請參閱[記錄檢視](../data/record-views-mfc-data-access.md)。

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>在文件與檢視中使用記錄集

許多簡單的基於表單的應用程式不需要文檔。 如果應用程式比較複雜,則可能需要將文檔用作資料庫的代理,儲存連接到數據`CDatabase`源的物件。 基於表單的應用程式通常將指向檢視中的記錄集物件的指標存儲。 其他類型的資料庫應用程式在文檔中儲存記錄集`CDatabase`和 物件。 以下是在資料庫應用程式中使用文件的一些可能性:

- 如果要訪問本地上下文中的記錄集,請根據需要在文檔或檢視的成員函數`CRecordset`中本地創建物件。

   將記錄集物件聲明為函數中的局部變數。 將 NULL 傳遞給建構函數,這將導致框架為您創建並`CDatabase`打開臨時 物件。 作為替代方法,將指標傳遞給物件`CDatabase`。 使用函數中的記錄集,並在函數退出時自動銷毀它。

   將 NULL 傳遞給記錄集建構函數時,框架將使用`GetDefaultConnect`記錄集 成員函數`CDatabase`傳回的資訊創建 物件並打開它。 匯為您實作`GetDefaultConnect`。

- 如果在文件的生存期內訪問記錄集,請將一個或多個`CRecordset`物件嵌入到文檔中。

   在初始化文檔時或根據需要構造記錄集物件。 如果記錄集已存在或構造,則可以編寫返回指向記錄集的指標的函數,如果記錄集尚不存在,則該函數將打開該記錄集。 根據需要關閉、刪除和重新創建記錄集,或調用其成員`Requery`函數刷新記錄。

- 如果在文件的生存期內訪問數據源,請嵌入`CDatabase`物件或存儲指向其中對`CDatabase`象的指標。

   該`CDatabase`物件管理與數據源的連接。 對象在文件建構期間自動建構,並在初始化文`Open`檔時調用其成員函數。 在文檔成員函數中建構記錄集物件時,會傳遞指向`CDatabase`文檔 物件的指標。 這將將每個記錄集與其數據源關聯。 資料庫物件通常在文檔關閉時銷毀。 記錄集物件通常會在退出函數範圍時銷毀它們。

## <a name="other-factors"></a><a name="_core_other_factors"></a>其他因素

基於表單的應用程式通常對框架的文件序列化機制沒有任何用,因此您可能需要刪除、關閉或取代**檔**檔案選單上的 **「新建**」和 **「打開」** 命令。 請參考文章[序列化:序列化與資料庫輸入/ 輸出](../mfc/serialization-serialization-vs-database-input-output.md)。

您可能還希望利用框架可以支援的許多用戶介面可能性。 例如,您可以在分割器視窗中使用`CRecordView`多個物件,在不同的多個文檔介面 (MDI) 子視窗中打開多個記錄集,等等。

您可能希望實現對檢視中任何內容的列印,無論是使用`CRecordView`或其他方式實現的形式。 由於派生自`CFormView`的`CRecordView`類不支援列印,但您可以重寫`OnPrint`成員函數以允許列印。 有關詳細資訊,請參閱類[CFormView](../mfc/reference/cformview-class.md)。

您可能根本不想要使用文檔和檢視。 在這種情況下,請參閱[MFC:使用沒有文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)。

## <a name="see-also"></a>另請參閱

[MFC 資料庫類別](../data/mfc-database-classes-odbc-and-dao.md)
