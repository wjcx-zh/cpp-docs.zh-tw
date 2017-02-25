---
title: "圖形物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HRGN"
  - "HFONT"
  - "HBITMAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "點陣圖 [C++], 在裝置內容中建立"
  - "筆刷, 在裝置內容中建立"
  - "CBitmap 類別, HBITMAP 控制代碼類型"
  - "CBrush 類別, HBRUSH 控制代碼類型"
  - "CFont 類別, HFONT 控制代碼類型"
  - "CPalette 類別, HPALETTE 控制代碼類型"
  - "CPen 類別, HPEN 控制代碼類型"
  - "CRgn 類別, HRGN 控制代碼類型"
  - "裝置內容, 圖形物件"
  - "繪製, 在裝置內容中"
  - "字型 [C++], 在裝置內容中建立"
  - "GDI [C++], 圖形物件類別"
  - "GDI 物件 [C++]"
  - "GDI 物件 [C++], 圖形物件類別"
  - "圖形物件"
  - "圖形物件, 在裝置內容中建立"
  - "HBITMAP 和類別 CBitmap"
  - "HBRUSH 和類別 CBrush"
  - "HFONT 和類別 CFont"
  - "HPALETTE 和類別 CPalette"
  - "HPEN"
  - "HRGN"
  - "影像 [C++], 圖形物件"
  - "記憶體 [C++], 顯示內容"
  - "MFC, 圖形物件"
  - "物件 [C++], 圖形"
  - "物件 [C++], 圖形物件"
  - "繪製和裝置內容"
  - "調色盤物件"
  - "調色盤, 在裝置內容中建立"
  - "畫筆物件"
  - "畫筆, 在裝置內容中建立"
  - "區域物件"
  - "區域, 在裝置內容中建立"
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 圖形物件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows 在裝置內容中提供各式各樣的可用繪圖工具。  它提供可繪製線條的畫筆、可填滿內部的筆刷和可繪製文字的字型。  MFC 提供相當於 Windows 中繪圖工具的圖形物件類別。  下表顯示可用的類別和對等的 Windows 繪圖裝置介面 \(GDI\) 控制代碼類型。  
  
> [!NOTE]
>  GDI\+ 隨附於 Windows XP 中，並且可做為 Windows NT 4.0 SP6、Windows 2000、Windows 98 和 Windows Me 的可轉散發套件。  若要下載最新版本的可轉散發套件，請參閱 [http:\/\/www.microsoft.com\/msdownload\/platformsdk\/sdkupdate\/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm)。  如需詳細資訊，請參閱 MSDN 中的 GDI\+ SDK 文件：[http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/gdicpp\/GDIPlus\/GDIPlus.asp](http://msdn.microsoft.com/library/default.asp?url=/library/gdicpp/GDIPlus/GDIPlus.asp)。  
  
 這篇文章說明如何使用這些圖形物件類別：  
  
### Windows GDI 物件的類別  
  
|類別|Windows 控制代碼類型|  
|--------|--------------------|  
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|  
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|  
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|  
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|  
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|  
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|  
  
> [!NOTE]
>  類別 [CImage](../atl-mfc-shared/reference/cimage-class.md) 提供增強的點陣圖支援。  
  
 類別庫中的每個圖形物件類別都有一個建構函式，可讓您建立該類別的圖形物件，接著您必須使用適當的建立函式來初始化，例如 `CreatePen`。  
  
 類別庫中的每個圖形物件類別都具有一個轉型運算子，可將MFC 物件轉型成相關聯的 Windows 控制代碼。  除非相關聯的物件與產生的控制代碼中斷連結，否則產生的控制代碼無效。  使用物件的 **Detach** 成員函式來中斷連結控制代碼。  
  
 下列程式碼會將 `CPen` 物件轉型成 Windows 控制代碼：  
  
 [!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/CPP/graphic-objects_1.cpp)]  
  
#### 在裝置內容中建立圖形物件  
  
1.  在堆疊框架上定義圖形物件。  使用類型特有的建立函式來初始化物件，例如 `CreatePen`。  此外，初始化建構函式中的物件。  請參閱[一階段和兩階段建立](../mfc/one-stage-and-two-stage-construction-of-objects.md)的討論，其提供一個程式碼範例。  
  
2.  [選取將放入目前的裝置內容的物件](../mfc/selecting-a-graphic-object-into-a-device-context.md)，儲存之前選取的舊圖形物件。  
  
3.  完成目前的圖形物件時，選取將舊圖形物件放回裝置內容中，以便還原其狀態。  
  
4.  允許在結束範圍時，自動刪除框架配置的圖形物件。  
  
> [!NOTE]
>  如果您將重複使用某個圖形物件，您可以配置它一次，並在每次需要時，選擇將該物件放入裝置內容中。  當您不再需要時，請務必刪除這類物件。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [圖形物件的一階段和兩階段建構](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [以一階段和兩階段建構畫筆的範例](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [選取圖形物件放入裝置內容中](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [裝置內容](../mfc/device-contexts.md)  
  
-   [舊版作業系統上的 CImage 限制](../mfc/cimage-limitations-with-earlier-operating-systems.md)  
  
## 請參閱  
 [視窗物件](../mfc/window-objects.md)