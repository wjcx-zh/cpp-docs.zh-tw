---
title: "剪貼簿： 使用 Windows 剪貼簿 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6063a27495d46e4b54f3133b92689e4b0faaa631
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-using-the-windows-clipboard"></a>剪貼簿：使用 Windows 剪貼簿
本主題描述如何使用標準 Windows 剪貼簿 API，MFC 應用程式中。  
  
 大部分 Windows 應用程式支援剪下或複製資料到 Windows 剪貼簿並貼上剪貼簿的資料。 剪貼簿資料格式是根據應用程式而異。 架構支援有限的數目的剪貼簿 格式的有限數目的類別。 您通常會實作的剪貼簿相關的命令 — 剪下、 複製和貼上 — 在您檢視的 [編輯] 功能表上。 類別庫會定義這些命令的命令 Id: **ID_EDIT_CUT**， **ID_EDIT_COPY**，和**ID_EDIT_PASTE**。 也會定義其訊息列提示字元。  
  
 [訊息和架構中的命令](../mfc/messages-and-commands-in-the-framework.md)說明如何將功能表命令對應至處理常式函式處理應用程式中的功能表命令。 只要您的應用程式不會定義在 [編輯] 功能表上的剪貼簿命令的處理常式函式，它們會維持已停用。 若要撰寫的剪下和複製命令的處理常式函式，請在應用程式中實作選取項目。 若要撰寫貼上 命令的處理常式函式，查詢剪貼簿，以查看它是否包含您的應用程式可接受的格式的資料。 例如，若要啟用 [複製] 命令，您可以撰寫處理常式像下面這樣：  
  
 [!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]  
  
 剪下、 複製和貼上命令只會在特定內容中有意義的。 只有在選取的項目，並貼上 命令時，才項目處於剪貼簿時，應該啟用剪下和複製命令。 您可以提供這項行為定義更新處理常式函式可啟用或停用這些命令，視內容而定。 如需詳細資訊，請參閱[如何更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)。  
  
 Microsoft Foundation 類別庫提供文字編輯與剪貼簿支援`CEdit`和`CEditView`類別。 OLE 類別也可以簡化實作剪貼簿流作業涉及 OLE 項目。 如需有關 OLE 類別的詳細資訊，請參閱[剪貼簿： 使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)。  
  
 實作其他編輯功能表命令，例如復原 (**ID_EDIT_UNDO**) 和取消復原 (**ID_EDIT_REDO**)，也會保留給您。 如果您的應用程式不支援這些命令，您可以輕鬆地刪除它們從您使用 Visual c + + 資源編輯器的資源檔。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [複製並貼上資料](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
## <a name="see-also"></a>請參閱  
 [剪貼簿](../mfc/clipboard.md)

