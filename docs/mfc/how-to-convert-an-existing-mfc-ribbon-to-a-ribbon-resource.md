---
title: 如何：將現有的 MFC 功能區轉換為功能區資源
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
ms.openlocfilehash: 2ba2907a95018948670847282fd09e0a71a8c106
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509552"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>如何：將現有的 MFC 功能區轉換為功能區資源

功能區資源比手動撰寫功能區程式碼更容易視覺化、修改和維護。 本主題說明如何將 MFC 專案中手動撰寫的功能區程式碼轉換為功能區資源。

您必須擁有現有的 MFC 專案，例如使用 MFC 功能區類別的程式碼[CMFCRibbonBar 類別](../mfc/reference/cmfcribbonbar-class.md)。

### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>將 MFC 功能區轉換為功能區資源

1. 在 Visual Studio 中，開啟 現有的 MFC 專案中的 原始程式檔位置`CMFCRibbonBar`物件初始化。 通常該檔案會是 mainfrm.cpp。 在功能區的初始化程式碼後面加入下列程式碼。

```
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");

```

   儲存並關閉檔案。

1. 建置並執行 MFC 應用程式，然後在 [記事本] 中，開啟 RibbonOutput.txt 並複製其內容。

1. 在 Visual Studio 中，在**專案**功能表上，按一下**加入資源**。 在 **加入資源**對話方塊中，選取**功能區**，然後按一下 **新增**。

   Visual Studio 會建立功能區資源並在設計檢視中將它開啟。 功能區資源識別碼是 IDR_RIBBON1，這會顯示在**資源檢視**。 功能區會在 ribbon1.mfcribbon-ms XML 檔案中定義。

1. 在 Visual Studio 中開啟 ribbon1.mfcribbon-ms，刪除其內容，然後貼上您先前複製之 RibbonOutput.txt 的內容。 儲存並關閉 ribbon1.mfcribbon-ms。

1. 再次開啟初始化 CMFCRibbonBar 物件的原始程式檔 (通常為 mainfrm.cpp) 並將現有的功能區程式碼標記為註解。 在標記為註解的程式碼後面加入下列程式碼。

```
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

```

1. 建置專案並執行程式。

## <a name="see-also"></a>另請參閱

[功能區設計工具 (MFC)](../mfc/ribbon-designer-mfc.md)

