---
title: "配置 GDI 資源 | Microsoft Docs"
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
  - "GDI 物件, 列印期間配置"
  - "列印 [MFC], 配置 GDI 資源"
  - "資源 [MFC], 列印"
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 配置 GDI 資源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何配置和取消配置列印所需的 Windows 圖形裝置介面 \(GDI\) 物件。  
  
> [!NOTE]
>  GDI\+ 隨附於 Windows XP 中，並且可做為 Windows NT 4.0 SP6、Windows 2000、Windows 98 和 Windows Me 的可轉散發套件。  若要下載最新版本的可轉散發套件，請參閱 [http:\/\/www.microsoft.com\/msdownload\/platformsdk\/sdkupdate\/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm)。  如需詳細資訊，請參閱 MSDN 中的 GDI\+ SDK 文件：[http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/gdicpp\/GDIPlus\/GDIPlus.asp](http://msdn.microsoft.com/library/default.asp?url=/library/gdicpp/GDIPlus/GDIPlus.asp)。  
  
 假設您需要使用特定字型、畫筆或其他 GDI 物件進行列印，但不用於螢幕顯示。  在應用程式啟動時配置這些物件需要較多記憶體，因此不符合效益。  當應用程式未列印文件時，這些記憶體可能需要用於其他用途。  在列印開始時配置這些物件，然後在列印結束時加以刪除，是較理想的做法。  
  
 若要配置這些 GDI 物件，請覆寫 [OnBeginPrinting](../Topic/CView::OnBeginPrinting.md) 成員函式。  此函式很適合此用途的原因有二： 架構會在每個列印工作開始時呼叫此函式一次，而且不同於 [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)，此函式可存取代表印表機裝置驅動程式的 [CDC](../mfc/reference/cdc-class.md) 物件。  您可以在檢視類別中定義指向 GDI 物件的成員變數在 \(例如 **CFont\*** 成員等等\)，以儲存這些物件供列印工作使用。  
  
 若要使用您已建立的 GDI 物件，請將其選取至 [OnPrint](../Topic/CView::OnPrint.md) 成員函式的印表機裝置內容中。  如果文件的不同頁面需要不同的 GDI 物件，您可以查看 [CPrintInfo](../mfc/reference/cprintinfo-structure.md) 結構的 `m_nCurPage` 成員，並據以選取 GDI 物件。  如果您的數個連續頁面需要某個 GDI 物件，Windows 會要求您在每次呼叫 `OnPrint` 時將其選取至裝置內容中。  
  
 若要取消配置這些 GDI 物件，請覆寫 [OnEndPrinting](../Topic/CView::OnEndPrinting.md) 成員函式。  架構會每個列印工作結束時呼叫此函式，讓您有機會在應用程式回到其他工作之前取消配置列印特定 GDI 物件。  
  
## 請參閱  
 [列印](../mfc/printing.md)   
 [如何完成預設列印](../mfc/how-default-printing-is-done.md)