---
title: "變更清單控制項樣式 | Microsoft Docs"
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
  - "CListCtrl 類別, 變更樣式"
  - "CListCtrl 類別, 樣式"
  - "樣式, CListCtrl"
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 變更清單控制項樣式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以隨時變更清單控制項 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 的視窗樣式，在您建立它之後。  藉由變更視窗樣式，變更控制項使用的檢視類型。  例如，模擬總管\]，您可以提供功能表項目或工具列按鈕切換控制的不同檢視之間:圖示檢視，清單檢視，依此類推。  
  
 例如，在中，當使用者選取的功能表項目時，您可以呼叫 [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) 擷取控制項的目前模式接著呼叫 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) 重設這個樣式。  在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]\(如需詳細資訊，請參閱 [使用清單檢視控制項](http://msdn.microsoft.com/library/windows/desktop/bb774736) 。  
  
 可用樣式在 [建立](../Topic/CListCtrl::Create.md)中。  樣式 `LVS_ICON`、 `LVS_SMALLICON`、 `LVS_LIST`和 `LVS_REPORT` 會指定四個清單控制項檢視中。  
  
## 延伸樣式  
 除了清單控制項的標準模式外，還有另一個集合，稱為延伸樣式。  這些樣式，討論在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [延伸清單檢視模式](http://msdn.microsoft.com/library/windows/desktop/bb774732) ，提供自訂的清單控制項行為的各種有用的功能。  若要實作某些樣式的行為 \(例如暫留選擇\)，請呼叫 [CListCtrl::SetExtendedStyle](../Topic/CListCtrl::SetExtendedStyle.md)，以傳遞這個需要的樣式。  下列範例示範函式呼叫:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/CPP/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  若要讓暫留的選取範圍，您也必須 **LVS\_EX\_ONECLICKACTIVATE** 和 **LVS\_EX\_TWOCLICKACTIVATE** 開啟。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)