---
title: "設定個別項目的影像 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "擴充的下拉式方塊, 影像"
  - "影像 [C++], 下拉式方塊項目"
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 設定個別項目的影像
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

展開的下拉式方塊項目使用的不同影像類型取決於 `iImage`、 **iSelectedImage**和 [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) 結構的 **iOverlay** 成員的值。  每個值為影像的索引控制項關聯的影像清單的。  根據預設，這些成員不是設定為 0，使控制項顯示項目的影像。  如果您想要針對特定項目使用影像，可以適當修改結構，其中一個，當插入下拉式方塊項目時或修改現有的下拉式方塊項目。  
  
## 將新項目加入影像  
 如果您要插入新的項目，請使用 `iImage`、 **iSelectedImage**和 **iOverlay** 結構成員有適當的值然後插入項目與呼叫 [CComboBoxEx::InsertItem](../Topic/CComboBoxEx::InsertItem.md)。  
  
 下列範例會插入新的展開的下拉式方塊項目 \(`cbi`\) 的展開的下拉式方塊控制項 \(`m_comboEx`\)，提供所有三個影像狀態的索引:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/CPP/setting-the-images-for-an-individual-item_1.cpp)]  
  
## 設定現有項目的影像  
 如果您修改現有的項目，您必須使用 **COMBOBOXEXITEM** 結構的 **mask** 成員。  
  
#### 修改現有的項目使用影像  
  
1.  **COMBOBOXEXITEM** 宣告結構並將 **mask** 資料成員對要修改感興趣的值。  
  
2.  使用這個類別，請呼叫 [CComboBoxEx::GetItem](../Topic/CComboBoxEx::GetItem.md)。  
  
3.  使用適當的值，修改 **mask**、 `iImage`和最近傳回結構的 **iSelectedImage** 成員。  
  
4.  呼叫 [CComboBoxEx::SetItem](../Topic/CComboBoxEx::SetItem.md)，本修改結構。  
  
 下列範例會交換第三個擴充的下拉式方塊項目的選取或未選取的影像示範這個程序:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/CPP/setting-the-images-for-an-individual-item_2.cpp)]  
  
## 請參閱  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控制項](../mfc/controls-mfc.md)