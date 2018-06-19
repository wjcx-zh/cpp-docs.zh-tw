---
title: 架構 (MFC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd75d29ce907b089d698c066e5a6cb41fcae3281
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344392"
---
# <a name="framework-mfc"></a>架構 (MFC)
您會使用 MFC 程式庫架構進行的工作有很大部分是基於一些主要類別和數個 Visual C++ 工具。 某些類別會封裝大部分的 Win32 應用程式開發介面 (API)。 其他類別會封裝應用程式概念 (例如文件、檢視和應用程式本身)。 而其餘的類別則會封裝 OLE 功能、ODBC 和 DAO 資料存取功能。  
  
 例如，視窗的 Win32 概念是由 MFC 類別 `CWnd` 所封裝。 也就是說，一個名為 `CWnd` 的 C++ 類別會封裝或「包裝」代表 Windows 視窗的 `HWND` 控制代碼。 同樣地，類別 `CDialog` 會封裝 Win32 對話方塊。  
  
 封裝表示 C++ 類別 (例如 `CWnd`) 包含 `HWND` 類型的成員變數，而類別的成員函式則是會封裝對採用 `HWND` 做為參數的 Win32 函式呼叫。 類別成員函式通常與它們所封裝的 Win32 函式具有相同名稱。  
  
## <a name="in-this-section"></a>本節內容  
 [SDI 和 MDI](../mfc/sdi-and-mdi.md)  
  
 [文件、檢視和架構](../mfc/documents-views-and-the-framework.md)  
  
 [精靈和資源編輯器](../mfc/wizards-and-the-resource-editors.md)  
  
## <a name="in-related-sections"></a>相關章節  
 [在架構上建置](../mfc/building-on-the-framework.md)  
  
 [架構如何呼叫您的程式碼](../mfc/how-the-framework-calls-your-code.md)  
  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)  
  
 [文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)  
  
 [訊息處理和對應](../mfc/message-handling-and-mapping.md)  
  
 [視窗物件](../mfc/window-objects.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)
