---
title: "在快速鍵對應表中加入項目 | Microsoft Docs"
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
  - "新增項目快速鍵對應表 [c + +]"
  - "新增快速鍵命令"
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在快速鍵對應表中加入項目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### <a name="to-add-an-entry-to-an-accelerator-table"></a>在快速鍵對應表中加入項目  
  
1.  開啟快速鍵對應表，其在圖示上按兩下 [資源檢視](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  快速鍵對應表內按一下滑鼠右鍵，然後選擇 [ **新加速器** 從捷徑功能表或按一下底部的資料表的空白資料列項目。  
  
3.  選取 [識別碼](Id%20Property.xml) 從 id 下拉式清單方塊或輸入新的識別碼在 **識別碼** 方塊。  
  
4.  型別 [金鑰](../windows/accelerator-key-property.md) 您想要做為快速鍵或以滑鼠右鍵按一下，然後選擇 [ **下一個按鍵輸入** 從捷徑功能表，以設定索引鍵的組合 ( **下一個按鍵輸入** 命令也會有 **編輯** 功能表)。  
  
5.  變更 [修飾詞](../windows/accelerator-modifier-property.md) 和 [類型](../windows/accelerator-type-property.md), ，如有必要。  
  
6.  按下 **ENTER**。  
  
    > [!NOTE]
    >  確定定義的所有快速鍵都是唯一的。 您可以有數個按鍵組合，指派給相同的 ID 而不會有不良影響，例如，CTRL + P 和 F8 可以同時指派給 ID_PRINT。 不過，將一個按鍵組合指派給多個 ID 將無法運作，例如，將 CTRL + Z 指派給 ID_SPELL_CHECK 和 ID_THESAURUS。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》 [](../Topic/Resources%20in%20Desktop%20Apps.md) 中的 *應用程式中的資源* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [Walkthrough: Using Resources for Localization with ASP。NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **Requirements**  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [編輯快速鍵對應表](../windows/editing-accelerator-tables.md)   
 [快速鍵編輯器](../mfc/accelerator-editor.md)