---
title: "剪貼簿 |Microsoft 文件"
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
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 304f20f94880b0bd8cb671788c5c06b69d25d377
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard"></a>剪貼簿
此系列文章說明如何在 MFC 應用程式中實作 Windows 剪貼簿的支援。 兩種方式使用 Windows 剪貼簿：  
  
-   實作標準編輯功能表命令，例如剪下、 複製和貼。  
  
-   實作統一的資料傳輸與拖曳拖放 (OLE)。  
  
 剪貼簿是在來源與目的地之間傳輸資料的標準 Windows 方法。 它也可以在 OLE 作業中很有用。 使用 OLE 的問世，有兩種剪貼簿機制在 Windows 中。 標準 Windows 剪貼簿 API 仍然可用，但它有已增添 OLE 資料傳輸機制。 OLE 制式資料傳輸 (UDT) 支援剪下、 複製和貼上剪貼簿和拖放。  
  
 剪貼簿是共用的整個 Windows 工作階段，因此它並沒有控制代碼或它自己的類別的系統服務。 管理類別成員函式透過剪貼簿[CWnd](../mfc/reference/cwnd-class.md)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [何時使用每個剪貼簿機制](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [使用傳統的 Windows 剪貼簿 API](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [複製並貼上資料](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [加入其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [Windows 剪貼簿](https://msdn.microsoft.com/library/ms648709)  
  
-   [實作拖放 (OLE)](../mfc/drag-and-drop-ole.md)  
  
## <a name="see-also"></a>請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)
