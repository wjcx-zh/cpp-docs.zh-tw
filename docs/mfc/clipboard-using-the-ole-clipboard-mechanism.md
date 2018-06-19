---
title: 剪貼簿： 使用 OLE 剪貼簿機制 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4940c614046e3ca407887e05e84c811a156d9c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342533"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>剪貼簿：使用 OLE 剪貼簿機制
OLE 使用標準格式和部分 OLE 特定格式來透過剪貼簿傳輸資料。  
  
 當您將剪下或複製應用程式中的資料時，資料會儲存在剪貼簿上以便稍後在貼上作業中使用。 這個資料會有各種格式。 當使用者選取貼上剪貼簿中的資料時，應用程式可以選擇使用哪一種格式。 除非使用者明確要求某種格式，否則應使用 [選擇性貼上] 寫入應用程式以選擇提供最多資訊的格式。 在繼續之前，您可能想要讀取[資料物件和資料來源 (OLE)](../mfc/data-objects-and-data-sources-ole.md)主題。 那些主題說明在應用程式中資料傳輸如何運作以及如何實作等基本知識。  
  
 Windows 會定義數種標準格式，可用於透過剪貼簿傳輸資料。 這些包括中繼檔、文字和點陣圖等。 OLE 也定義許多 OLE 特定格式。 對於除了這些標準格式外還需要提供更詳細資料的應用程式，最好能註冊它們自己的自訂剪貼簿格式。 使用 Win32 API 函式[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)若要這樣做。  
  
 例如，Microsoft Excel 會註冊試算表的自訂格式。 這個格式會傳輸比諸如點陣圖更多更詳細的資訊。 將這個資料貼入支援試算表格式的應用程式時，試算表的所有公式和值都會保留且可在必要時進行更新。 Microsoft Excel 放在剪貼簿上的資料格式也可以貼成 OLE 項目。 所有 OLE 文件容器都可以將此資訊貼上為內嵌項目。 也可以使用 Microsoft Excel 變更此內嵌項目。 剪貼簿還包含試算表中所選取範圍的影像的簡單點陣圖。 這也可以貼入 OLE 文件容器或點陣圖編輯器 (如小畫家) 中。 不過，在點陣圖的情況下，沒有方法可將資料當做試算表來操作。  
  
 若要從剪貼簿擷取最大量的資訊，應用程式應該在從剪貼簿貼上資料之前，先檢查這些自訂格式。  
  
 例如，若要啟用 [剪下] 命令，您可以撰寫類似如下的處理常式：  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [複製並貼上資料](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [加入其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [使用 Windows 剪貼簿](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [OLE 資料物件和資料來源和制式資料傳輸](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>另請參閱  
 [剪貼簿](../mfc/clipboard.md)

