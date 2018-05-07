---
title: 自訂標頭項目&#39;s 外觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b58af1efc0558fe9195f56c31df11827d57f731
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-the-header-item39s-appearance"></a>自訂標頭項目&#39;s 外觀
藉由設定*dwStyle*參數，當您初次建立標題控制項 ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create))、 您可以定義的外觀和行為的標頭項目，或標頭控制本身。  
  
 以下是可設定之樣式的示範及其用途：  
  
-   若要讓標題項目看起來像按鈕，請使用 `HDS_BUTTONS` 樣式。  
  
     如果您要執行動作來回應標題項目上的滑鼠點選作業，例如 Microsoft Outlook 中以特定欄排序資料，請使用這個樣式。  
  
-   若要指定當滑鼠指標通過時標題項目有「熱追蹤」外觀，請使用 `HDS_HOTTRACK` 樣式。  
  
     熱追蹤會在平面的標題列上，於指標通過項目時顯示 3D 外框。  
  
-   若要指出標題控制項應被隱藏，請使用 `HDS_HIDDEN` 樣式。  
  
     `HDS_HIDDEN` 樣式表示標題控制項做為資料容器而非視覺控制項。 這個樣式不會自動隱藏控制項，而是會影響 `CHeaderCtrl::Layout` 的行為。 中傳回的值**cy**隸屬`WINDOWPOS`結構將會是零，表示控制項不應該顯示給使用者。  
  
 如需有關這些屬性的詳細資訊，請參閱[項目](http://msdn.microsoft.com/library/windows/desktop/bb775238)Windows SDK 中。 將項目加入至標題控制項的相關資訊，請參閱[將項目加入至標題控制項](../mfc/adding-items-to-the-header-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

