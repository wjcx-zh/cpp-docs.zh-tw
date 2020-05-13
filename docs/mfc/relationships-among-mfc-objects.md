---
title: MFC 物件關聯性
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: d7e40e25b405d3f8ec50a518889cc2b89bc8c725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372817"
---
# <a name="relationships-among-mfc-objects"></a>MFC 物件關聯性

為了協助放置文件/檢視建立程序，請考慮一個執行中程式：一個文件、一個用來包含檢視的框架視窗，以及與文件關聯的檢視。

- 文件會保留該文件的檢視清單，以及一個指向已建立之文件的文件範本的指標。

- 檢視會保留指向其文件的指標，而且是其父框架視窗的子系。

- 文件框架視窗會保留指向其目前現用檢視的指標。

- 文件範本會保留其開啟的文件清單。

- 應用程式會保留其文件範本的清單。

- Windows 會持續追踨所有開啟的視窗，因此可以傳送訊息給它們。

這些關聯性是在文件/檢視建立期間建立。 下表顯示執行中程式的物件如何存取其他物件。 任何物件都可以通過調用全域函數[AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp)獲得指向應用程式物件的指標。

### <a name="gaining-access-to-other-objects-in-your-application"></a>存取應用程式中的其他物件

|來源物件|如何存取其他物件|
|-----------------|---------------------------------|
|Document|使用[GetFirst 查看位置](../mfc/reference/cdocument-class.md#getfirstviewposition)和[GetNextView](../mfc/reference/cdocument-class.md#getnextview)訪問文檔的檢視清單。<br /><br /> 致電[GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate)獲取文檔範本。|
|檢視|致電[GetDocument](../mfc/reference/cview-class.md#getdocument)獲取文檔。<br /><br /> 調用[獲取父框架](../mfc/reference/cwnd-class.md#getparentframe)以獲取幀視窗。|
|文件框架視窗|致電[獲取活動檢視](../mfc/reference/cframewnd-class.md#getactiveview)以獲取當前檢視。<br /><br /> 呼叫[GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument)獲取文件附加到當前檢視。|
|MDI 框架視窗|執行電[MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive)取得目前處於活動狀態的[CMDIChildwnd](../mfc/reference/cmdichildwnd-class.md)。|

通常框架視窗會有一個檢視，不過有時候在分隔視窗中，同一個框架視窗會包含多個檢視。 框架視窗會保留目前使用中檢視的指標，該指標會在其他檢視啟動時的進行更新。

> [!NOTE]
> 指向主框架視窗的指標存儲在應用程式物件的[m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd)成員變數中。 `OnFileNew``InitInstance`在`CWinApp`*重寫集的成員*函數時,m_pMainWnd調用。 如果您未呼叫 `OnFileNew`，則必須自己在 `InitInstance` 中設定變數值 (如果 /嵌入位於命令列上,則 SDI COM 元件(伺服器)應用程式可能無法設置變數。請注意 *,m_pMainWnd*現在`CWinThread`是類 的`CWinApp`成員,而不是 。

## <a name="see-also"></a>另請參閱

[文件樣本與文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文件樣板建立](../mfc/document-template-creation.md)<br/>
[文件/檢視建立](../mfc/document-view-creation.md)<br/>
[建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)
