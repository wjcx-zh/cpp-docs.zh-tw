---
title: "Class Factory 和授權 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Class Factory, 和授權"
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Class Factory 和授權
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要建立您的 OLE automation 控制項執行個體，容器應用程式呼叫控制項的 Class Factory 的成員函式。  由於您的控制項是實際 OLE 物件， Class Factory 以建立您的控制項執行個體。  每個 OLE automation 控制項類別必須有 Class Factory。  
  
 OLE automation 控制項另一個重要功能是其能力強制執行授權。  ControlWizard 可讓您控制在專案建立期間合併授權。  如需您所建立的控制項授權的詳細資訊，請參閱[授權 ActiveX 控制項：ActiveX 控制項授權](../../mfc/mfc-activex-controls-licensing-an-activex-control.md) 的文章。  
  
 下表列出用於數個巨集和函式宣告和實作控制項的 Class Factory 和加入控制項的授權。  
  
### Class Factory 和授權  
  
|||  
|-|-|  
|[DECLARE\_OLECREATE\_EX](../Topic/DECLARE_OLECREATE_EX.md)|宣告 OLE automation 控制項或屬性頁的 Class Factory。|  
|[IMPLEMENT\_OLECREATE\_EX](../Topic/IMPLEMENT_OLECREATE_EX.md)|實作控制項的 `GetClassID` 函式宣告 Class Factory 的執行個體。|  
|[BEGIN\_OLEFACTORY](../Topic/BEGIN_OLEFACTORY.md)|啟動所有允許函式的宣告。|  
|[END\_OLEFACTORY](../Topic/END_OLEFACTORY.md)|結束所有允許函式的宣告。|  
|[AfxVerifyLicFile](../Topic/AfxVerifyLicFile.md)|驗證控制項是否允許為在特定電腦上使用。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)