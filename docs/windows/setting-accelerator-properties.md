---
title: "設定快速鍵屬性 | Microsoft Docs"
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
  - "快速鍵屬性"
  - "屬性 [c + +] 快速鍵屬性"
  - "Type 屬性"
  - "Key 屬性"
  - "Modifier 屬性"
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 設定快速鍵屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual c + +.NET 中，您可以設定快速鍵屬性 [屬性] 視窗](../Topic/Properties%20Window.md) 在任何時間。 您也可以使用快速鍵編輯器來修改快速鍵對應表中的快速鍵屬性。 使用 [屬性] 視窗或快速鍵編輯器所做的變更會有相同的結果：編輯會立即反映在快速鍵對應表中。  
  
 有三個屬性的每個加速器 [識別碼](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-    [輔助按鍵屬性](../windows/accelerator-modifier-property.md) 設定控制項的快速鍵組合。  
  
    > [!NOTE]
    >  在 [屬性] 視窗中，這個屬性會顯示為三個不同的布林值屬性，且三個屬性都可以獨立控制：Alt、Ctrl 和 Shift 鍵。  
  
-    [索引鍵屬性](../windows/accelerator-key-property.md) 設定做為快速鍵實際的金鑰。  
  
-    [型別屬性](../windows/accelerator-type-property.md) 判斷是否要將索引鍵解譯成虛擬 ([virtkey]) 或 ASCII/ANSI。  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》 [](../Topic/Resources%20in%20Desktop%20Apps.md) 中的 *應用程式中的資源* 。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱 [Walkthrough: Using Resources for Localization with ASP。NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [預先定義的快速鍵](../windows/predefined-accelerator-keys.md)   
 [資源編輯器](../mfc/resource-editors.md)   
 [快速鍵編輯器](../mfc/accelerator-editor.md)