---
title: "連接對應 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "連接對應"
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 連接對應
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 控制項可以公開介面在其他應用程式。  這些介面只允許從容器存取該控制項。  如果 OLE 控制項要存取其他 OLE 物件外部介面，連接點必須建立。  這個連接點允許外部分派對應的控制項上存取，例如事件對應或告知函式。  
  
 MFC 程式庫提供支援的連接點的程式設計模型。  在這個模型中， 「連接對應」用於指定介面或 OLE 控制項的連接點。  連結導覽中每個連接點的巨集。  如需連接對應的詳細資訊，請參閱 [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) 類別。  
  
 通常，控制項會支援兩個連接點:傳回集合中第一個屬性的告知。  這些由 `COleControl` 基底類別實作且由控制項寫入器不需要額外的工作。  在您的類別要實作的連接點必須手動加入。  若要支援連接對應和點， MFC 提供下列巨集:  
  
### 連接對應宣告和分界  
  
|||  
|-|-|  
|[BEGIN\_CONNECTION\_PART](../Topic/BEGIN_CONNECTION_PART.md)|宣告實作其他連接點的內嵌類別 \(必須在類別宣告\)。|  
|[END\_CONNECTION\_PART](../Topic/END_CONNECTION_PART.md)|結束連接點的宣告 \(必須在類別宣告\)。|  
|[CONNECTION\_IID](../Topic/CONNECTION_IID.md)|指定控制項的連接點的介面 ID。|  
|[DECLARE\_CONNECTION\_MAP](../Topic/DECLARE_CONNECTION_MAP.md)|宣告連接對應來類別 \(必須在類別宣告\)。|  
|[BEGIN\_CONNECTION\_MAP](../Topic/BEGIN_CONNECTION_MAP.md)|啟動連接對應的定義 \(必須使用類別實作\)。|  
|[END\_CONNECTION\_MAP](../Topic/END_CONNECTION_MAP.md)|結束連接對應的定義 \(必須使用類別實作\)。|  
|[CONNECTION\_PART](../Topic/CONNECTION_PART.md)|指定在控制項的連接對應的連接點。|  
  
 使用連接點，下列函式以協助建立和中斷連接之接收:  
  
### 連接點的初始化\/結束  
  
|||  
|-|-|  
|[AfxConnectionAdvise](../Topic/AfxConnectionAdvise.md)|建立來源和接收之間的連接。|  
|[AfxConnectionUnadvise](../Topic/AfxConnectionUnadvise.md)|中斷來源和接收之間的連接。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)