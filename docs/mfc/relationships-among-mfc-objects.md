---
title: "MFC 物件關聯性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ea93e9e56b676e4dfef33ecbcabfd9754458024
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="relationships-among-mfc-objects"></a>MFC 物件關聯性
為了協助放置文件/檢視建立程序，請考慮一個執行中程式：一個文件、一個用來包含檢視的框架視窗，以及與文件關聯的檢視。  
  
-   文件會保留該文件的檢視清單，以及一個指向已建立之文件的文件範本的指標。  
  
-   檢視會保留指向其文件的指標，而且是其父框架視窗的子系。  
  
-   文件框架視窗會保留指向其目前現用檢視的指標。  
  
-   文件範本會保留其開啟的文件清單。  
  
-   應用程式會保留其文件範本的清單。  
  
-   Windows 會持續追踨所有開啟的視窗，因此可以傳送訊息給它們。  
  
 這些關聯性是在文件/檢視建立期間建立。 下表顯示執行中程式的物件如何存取其他物件。 任何物件都可以藉由呼叫全域函式取得應用程式物件的指標[AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp)。  
  
### <a name="gaining-access-to-other-objects-in-your-application"></a>存取應用程式中的其他物件  
  
|來源物件|如何存取其他物件|  
|-----------------|---------------------------------|  
|文件|使用[GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition)和[GetNextView](../mfc/reference/cdocument-class.md#getnextview)存取文件的檢視清單。<br /><br /> 呼叫[GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate)取得文件範本。|  
|檢視|呼叫[GetDocument](../mfc/reference/cview-class.md#getdocument)取得文件。<br /><br /> 呼叫[GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe)以取得框架視窗。|  
|文件框架視窗|呼叫[GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) ，以取得目前的檢視。<br /><br /> 呼叫[GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument)取得附加至目前檢視的文件。|  
|MDI 框架視窗|呼叫[MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive)以取得目前使用中[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)。|  
  
 通常框架視窗會有一個檢視，不過有時候在分隔視窗中，同一個框架視窗會包含多個檢視。 框架視窗會保留目前使用中檢視的指標，該指標會在其他檢視啟動時的進行更新。  
  
> [!NOTE]
>  主框架視窗的指標儲存在[m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd)應用程式物件的成員變數。 在 `OnFileNew` 的 `InitInstance` 成員函式覆寫中呼叫 `CWinApp` 會為您設定 `m_pMainWnd`。 如果您未呼叫 `OnFileNew`，則必須自己在 `InitInstance` 中設定變數值 (如果命令列上存在 /Embedding，則 SDI COM 元件 (伺服器) 應用程式可能無法設定變數)。請注意，`m_pMainWnd` 現在是 `CWinThread` 類別的成員，而非 `CWinApp` 類別在的成員。  
  
## <a name="see-also"></a>請參閱  
 [文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [建立文件範本](../mfc/document-template-creation.md)   
 [文件/檢視建立](../mfc/document-view-creation.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)

