---
title: "自訂標題項目外觀 | Microsoft Docs"
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
  - "CHeaderCtrl 類別, 自訂項目"
  - "HDS_ 樣式"
  - "標題控制項, 項目自訂"
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 自訂標題項目外觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您先建立標題控制項 \([CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md)\) 時藉由設定 *dwStyle* 參數，您可以定義標頭項目的外觀和行為或標題控制項。  
  
 以下是您可以設定樣式的示範及其用途:  
  
-   若要將標題項目設成看起來像按鈕，請使用 `HDS_BUTTONS` 樣式。  
  
     如果您要執行滑鼠按一下標題項目的回應的動作，請使用這個樣式，例如以特定欄排序資料，如 Microsoft Outlook。  
  
-   若要指定當滑鼠指標通過時標題項目「熱追蹤」外觀，請使用 `HDS_HOTTRACK` 樣式。  
  
     熱追蹤於另外的水平棒上顯示作為通過項目的指標的 3D 外框。  
  
-   若要指出標題控制項應被隱藏，請使用 `HDS_HIDDEN` 樣式。  
  
     `HDS_HIDDEN` 樣式表示標題控制項做為資料容器而非視覺控制項。  這個樣式不會在控制項自動隱藏，相反地，會影響 `CHeaderCtrl::Layout`的行為。  在 `WINDOWPOS` 結構的 **cy** 成員傳回的值會是零表示控制項不應該顯示給使用者。  
  
 如需這些屬性的詳細資訊，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 中的 [Items](http://msdn.microsoft.com/library/windows/desktop/bb775238)。  如需加入項目至標題控制項的相關資訊，請參閱 [將項目加入至標題控制項](../mfc/adding-items-to-the-header-control.md)。  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)