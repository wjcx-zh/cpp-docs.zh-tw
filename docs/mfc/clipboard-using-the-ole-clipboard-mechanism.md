---
title: "剪貼簿：使用 OLE 剪貼簿機制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式 [OLE], 剪貼簿"
  - "剪貼簿 [C++], OLE 格式"
  - "格式 [C++], OLE 的剪貼簿"
  - "OLE 剪貼簿"
  - "OLE 剪貼簿, 格式"
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 剪貼簿：使用 OLE 剪貼簿機制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 使用標準格式和某些 OLE 特定格式的資料傳輸到剪貼簿。  
  
 當您將剪下或複製到應用程式中的資料時，資料會在貼上作業將使用的剪貼簿中。  這個資料會有各種格式。  當使用者選取貼上剪貼簿中的資料時，應用程式可以選擇使用哪一種格式。  應寫入應用程式來選擇提供大部分資訊格式，除非使用者明確地要求某種格式，來使用貼上特殊。  在繼續之前，您可能要讀取 [資料物件和資料來源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) 主題。  會在您的應用程式描述基本資料傳輸如何運作以及如何加以實作。  
  
 Windows 會定義可用於將資料使用剪貼簿的許多標準格式。  這些包括中繼檔、文字，點陣圖等。  OLE 定義了許多 OLE 特定格式。  如需比較這些標準格式給需要詳細資料的應用程式，最好能註冊它們自己的自訂剪貼簿格式。  使用 Win32 API 函式 [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) 來這樣做。  
  
 例如， Microsoft Excel 註冊報表的自訂格式。  這個格式會傳用詳細資訊，例如點陣圖。  這個資料貼入支援報告格式的應用程式時，所有公式和值從報表保留並可以在必要時更新。  Microsoft Excel 在剪貼簿也將資料格式，以便貼成 OLE 項目。  所有 OLE 文件容器可以貼上此資訊做為內嵌項目。  使用 Microsoft Excel，本內嵌的項目可以被變更。  剪貼簿也包含報表中的選取範圍的影像的簡單點陣圖。  這也可以貼入 OLE 文件容器或輸入點陣圖編輯器，像是繪製。  在點陣圖的情況下，不過，沒有方法可以以報告操作資料。  
  
 若要從剪貼簿擷取最大資訊，應用程式應該在貼上剪貼簿中的資料之前檢查這些自訂格式。  
  
 例如，若要剪下命令，您可以類似下列來撰寫處理常式:  
  
 [!code-cpp[NVC_MFCListView#3](../mfc/codesnippet/CPP/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [複製和貼上資料](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [加入其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [使用 Windows 剪貼簿](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [OLE 資料物件和資料來源以及一致的資料傳輸。](../mfc/data-objects-and-data-sources-ole.md)  
  
## 請參閱  
 [剪貼簿](../mfc/clipboard.md)