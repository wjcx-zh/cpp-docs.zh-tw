---
title: "Rich Edit 控制項中的段落格式化 | Microsoft Docs"
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
  - "CRichEditCtrl 類別, 其中的段落格式化"
  - "格式化 [C++], 段落"
  - "CRichEditCtrl 中的段落格式化"
  - "Rich Edit 控制項, 其中的段落格式化"
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Rich Edit 控制項中的段落格式化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的成員函式來格式化段落並擷取格式化資訊。  段落格式屬性包含對齊、選項、縮排和編號。  
  
 您可以使用 [SetParaFormat](../Topic/CRichEditCtrl::SetParaFormat.md) 成員函式，將段落格式化。  若要判斷所選取文字的目前段落格式，請使用 [GetParaFormat](../Topic/CRichEditCtrl::GetParaFormat.md) 成員函式。  [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) 結構用於搭配這些成員函式指定區段屬性。  其中一個 **PARAFORMAT** 的重要成員是 **dwMask**。  在 `SetParaFormat`中，指定哪些 **dwMask** 段落屬性會由這個函式呼叫設定。  `GetParaFormat` 報告第一個段落的屬性在選取範圍中；**dwMask** 指定一致的選取範圍中的屬性。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)