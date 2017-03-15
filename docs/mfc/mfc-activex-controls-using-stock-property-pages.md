---
title: "MFC ActiveX 控制項：使用內建屬性頁 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLSID_CPicturePropPage"
  - "CLSID_CColorPropPage"
  - "CLSID_CFontPropPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLSID_CColorPropPage"
  - "CLSID_CFontPropPage"
  - "CLSID_CPicturePropPage"
  - "色彩內建屬性頁"
  - "字型, ActiveX 控制項"
  - "MFC ActiveX 控制項, 屬性頁"
  - "圖片內建屬性頁"
  - "內建屬性, 內建屬性頁"
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：使用內建屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將討論股票屬性頁可用的 ActiveX 控制項和如何使用它們。  
  
 如需使用屬性頁的詳細資訊在 ActiveX 控制項，請參閱下列文件:  
  
-   [MFC ActiveX 控制項：屬性頁](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [MFC ActiveX 控制項：加入另一個自訂屬性頁](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC 提供三種內建屬性頁以使用 ActiveX 控制項: **CLSID\_CColorPropPage**、**CLSID\_CFontPropPage**和 **CLSID\_CPicturePropPage**。  這些頁面分別顯示股票色彩、字型和圖片屬性的使用者介面。  
  
 若要結合這些屬性頁加入至控制項，請將它們的 ID 加入至初始化控制項的陣列屬性頁 ID 的程式碼。  在下列範例中，此程式碼，位於控制項實作檔 \(.CPP\)，初始化陣列包含三個內建屬性頁和預設屬性頁 \(在本例中的具名 `CMyPropPage` \):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/CPP/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 請注意 Count 屬性頁，在 `BEGIN_PROPPAGEIDS` 巨集，是 4。  這表示屬性的頁數 ActiveX 控制項的支援。  
  
 在這些修改後，請重建專案。  您的控制項現在有字型、圖片和色彩屬性的屬性頁。  
  
> [!NOTE]
>  如果控制項內建屬性頁無法存取，可能是因為， MFC DLL \(MFCxx.DLL\) 未正確向目前作業系統登錄。  這通常來自於安裝 Visual C\+\+ 在不同目前正在執行的作業系統中使用。  
  
> [!TIP]
>  如果您的內建屬性頁不是可見的 \(請參閱先前的注意事項\)，請執行 RegSvr32.exe 註冊 DLL 以完整路徑名稱的命令列到 DLL。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：加入內建屬性](../mfc/mfc-activex-controls-adding-stock-properties.md)