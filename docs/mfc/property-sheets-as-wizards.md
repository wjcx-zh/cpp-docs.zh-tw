---
title: "屬性工作表做為精靈 | Microsoft Docs"
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
  - "屬性工作表, 做為精靈"
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 屬性工作表做為精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

索引鍵通常精靈屬性工作表是巡覽隨下或結束、後面和取消按鈕取代選項。  您必須在呼叫屬性工作表物件的 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) 之前使用這項功能就稱為 [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md) 。  
  
 使用者收到相同的 [CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md) 和 [CPropertyPage::OnKillActive](../Topic/CPropertyPage::OnKillActive.md) 告知，當將從一頁移至其他頁面時。  下個和結束按鈕是互斥的控制項;即一次只會顯示其中一個。  在第一頁，下一步按鈕應該啟用。  如果使用者為最後一頁，結束按鈕應該啟用。  這不是由架構會自動完成的。  您必須呼叫在最後一頁的 [CPropertySheet::SetWizardButton](../Topic/CPropertySheet::SetWizardButtons.md) 達成這個目的。  
  
 顯示所有預設按鈕，您必須示範關閉按鈕和將移動下一個按鈕。  然後移至上一頁按鈕，讓它與下個按鈕相對維護。  如需詳細說明，請搜尋知識庫文件 Q143210。  可以在 MSDN library 中尋找知識庫文件。  
  
## 範例  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/CPP/property-sheets-as-wizards_1.cpp)]  
  
## 請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)