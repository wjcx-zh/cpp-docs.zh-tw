---
title: "簡單資料類型類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料類別 [C++]"
  - "純量類別 [C++]"
  - "簡單資料類型類別"
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 簡單資料類型類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列類別會封裝繪圖協調，字串和時間和日期資訊，允許對 C\+\+ 語法的方便使用。  這些物件廣泛使用當做參數傳遞至視窗類別的成員函式在類別庫中。  由於 `CPoint`、 `CSize`和 `CRect` 對應、 **SIZE**和 **POINT**`RECT` 結構，分別，在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中，您可以使用這些 C\+\+ 類別物件的地方，您可以使用這些 C 語言結構。  類別透過其成員函式提供有用的介面。  `CStringT` 提供彈性動態字串。  `CTime`、 `COleDateTime`、 `CTimeSpan`和 **COleTimeSpan** 表示日期和時間值。  如需這些類別的詳細資訊，請參閱本文件的 [日期和時間。](../atl-mfc-shared/date-and-time.md)。  
  
 從「**COle**」開頭的類別是 OLE 所提供之資料型別的封裝。  這些資料型別可用於 Windows 程式不論是否使用其他 OLE 功能。  
  
 [CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)  
 保持字元字串。  
  
 [CTime](../atl-mfc-shared/reference/ctime-class.md)  
 保持絕對日期和時間值。  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 OLE Automation 型別 **DATE**的包裝函式。  表示日期和時間值。  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 保持相對日期和時間值。  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 表示相對於 `COleDateTime` 的值，例如兩個 `COleDateTime` 值之間的差異。  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 保持座標 \(x, y\)。  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 保持距離、相對位置或配對的值。  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 保持矩形區域的座標。  
  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 提供 Windows 影像清單的功能。  影像清單使用與清單控制項和樹狀目錄控制項。  也可以用來儲存和保存一組相同的點陣圖。  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 OLE Automation 型別 **VARIANT**的包裝函式。  在 **VARIANT**的資料可以用許多格式加以儲存。  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 OLE Automation 型別的 **CURRENCY** 的包裝函式，定點算術型別，它在小數點前有 15 位數及之後有 4 位數。  
  
> [!NOTE]
>  從 Visual C\+\+ .NET 開始，修改 `CRect`、 `CSize`和 `CPoint` 可在 ATL 或 MFC 應用程式。  此外， `CStringT` 將提供 MFC 獨立 `CString`像的類別。  如需共用的公用程式類別的詳細資訊，請參閱 [共用類別](../atl-mfc-shared/atl-mfc-shared-classes.md)。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)