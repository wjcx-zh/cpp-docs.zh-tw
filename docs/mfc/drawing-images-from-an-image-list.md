---
title: "從影像清單描繪影像 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImageList 類別, 繪圖影像來源"
  - "繪製, 影像清單的影像"
  - "影像清單 [C++], 繪圖影像來源"
  - "影像 [C++], 繪製"
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從影像清單描繪影像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要繪製影像，請使用 [CImageList::Draw](../Topic/CImageList::Draw.md) 成員函式。  您要指定指標裝置內容物件，影像的索引位置，繪製在繪製影像和一組旗標的繪製樣式的裝置內容。  
  
 當您指定 `ILD_TRANSPARENT` 樣式時， **Draw** 使用兩個步驟遮罩繪製影像。  首先，它會執行 AND 邏輯作業在影像的位元和位元遮罩。  然後它會在第一個作業的結果與目的裝置内容的背景位元的邏輯 XOR 運算。  這個程序會在產生的影像透明區域;即遮罩中每個白色位元組所產生的影像造成對應的位元透明。  
  
 在繪製純色背景的遮罩影像之前，您應該使用 [SetBkColor](../Topic/CImageList::SetBkColor.md) 成員函式將影像清單的背景色彩為色彩和目的相同。  設定色彩不需要建立在影像透明區域並使 **Draw** 複製至目的裝置内容，導致效能降低的明顯地增加。  當您呼叫 **Draw**時，若要繪製影像，請指定 `ILD_NORMAL` 樣式。  
  
 您可以隨時設定遮罩影像清單 \([CImageList](../mfc/reference/cimagelist-class.md)\) 背景色彩，以便在所有的背景純色正確繪製。  造成繪製影像上的預設設定為 `CLR_NONE` 的背景色彩。  若要擷取影像清單的背景色彩，請使用 [GetBkColor](../Topic/CImageList::GetBkColor.md) 成員函式。  
  
 使用系統的醒目提示色彩的影像的 `ILD_BLEND25` 和 `ILD_BLEND50` 樣式遞色。  這些樣式是有用的，如果您使用遮罩表示使用者可選取的物件。  例如，在中，當使用者選取控制項時，您可以使用 `ILD_BLEND50` 樣式來繪製影像。  
  
 使用 **SRCCOPY** 光柵作業，一 nonmasked 影像複製到目的裝置內容。  不論裝置內容的背景色彩，在影像的色彩出現相同。  在 **Draw** 指定的繪製樣式也會一 nonmasked 影像的外觀。  
  
 除了繪製成員函式之外，另一個函式， [DrawIndirect](../Topic/CImageList::DrawIndirect.md)，延伸能力呈現影像。  `DrawIndirect` ，會接受做為參數， [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) 結構。  這個結構可以用來自訂目前影像的呈現，包括使用光柵作業 \(ROP\) 程式碼。  如需 ROP 程式碼的詳細資訊，請參閱 [光柵作業程式碼](http://msdn.microsoft.com/library/windows/desktop/dd162892) 和 [點陣圖當做筆刷使用](http://msdn.microsoft.com/library/windows/desktop/dd183378) 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
## 請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)