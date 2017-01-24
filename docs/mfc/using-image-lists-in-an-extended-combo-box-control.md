---
title: "在擴充的下拉式方塊控制項中使用影像清單 | Microsoft Docs"
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
  - "影像清單 [C++], 下拉式方塊"
  - "影像 [C++], 下拉式方塊項目"
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在擴充的下拉式方塊控制項中使用影像清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

展開的下拉式方塊控制項主要功能是能夠關聯從影像清單中的影像與下拉式方塊控制項中的個別項目。  每個項目可以顯示三個影像:其中一個選取的狀態，其中一個 nonselected 狀態和覆疊影像的第三個。  
  
 下列程序關聯影像清單與展開的下拉式方塊控制項:  
  
### 若要使影像清單與展開的下拉式方塊控制項  
  
1.  建構新的影像清單 \(或使用現有的影像清單物件\) 使用 [CImageList](../mfc/reference/cimagelist-class.md) 建構函式和儲存結果指標，則為。  
  
2.  透過呼叫 [CImageList::Create](../Topic/CImageList::Create.md)初始化新的影像清單物件。  下列程式碼是這個呼叫的範例。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/CPP/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  將每個可能狀態的選擇性影像:選取或 nonselected 和覆疊。  下列程式碼加入三個預先定義的影像。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/CPP/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  相關聯的影像清單中具有名為的控制項為 [CComboBoxEx::SetImageList](../Topic/CComboBoxEx::SetImageList.md)。  
  
 一旦影像清單與控制項，您可以個別指定每一個項目為三個可能的狀態時所用的影像。  如需詳細資訊，請參閱 [設定個別項目的影像](../mfc/setting-the-images-for-an-individual-item.md)。  
  
## 請參閱  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控制項](../mfc/controls-mfc.md)