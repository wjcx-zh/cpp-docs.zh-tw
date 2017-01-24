---
title: "執行階段物件模型服務 | Microsoft Docs"
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
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "執行階段物件模型服務巨集"
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
caps.latest.revision: 15
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 執行階段物件模型服務
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CObject](../../mfc/reference/cobject-class.md) 和 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 類別封裝數個物件服務，包括對執行階段類別資訊、序列化和動態物件建立的存取。  從 `CObject` 衍生的類別會繼承這個功能。  
  
 對執行階段類別的資訊。可讓您決定物件類別的資訊在執行階段。  可判斷物件的類別在執行階段是有用的，當您需要額外型別檢查函式引數，但是，當您必須撰寫根據物件的類別中的程式碼。  執行階段類別資訊不會直接由 C\+\+ 語言支援。  
  
 序列化是常值或讀取處理物件的內容加入至檔案。  在應用程式結束之後，您可以使用序列化存放物件的內容。  當應用程式重新啟動時，物件可以從檔案讀取。  這類資料物件被視為持續性」。  
  
 動態物件建立可讓您建立指定類別的物件在執行階段。  例如，因為架構需要動態建立，這些文件、檢視和框架物件必須支援動態建立。  
  
 下表列出支援的執行階段類別資訊、序列化和動態建立的 MFC 巨集。  
  
 如需這些執行階段物件服務和序列化的詳細資訊，請參閱本文件的 [CObject 類別:存取的執行階段類別資訊](../../mfc/accessing-run-time-class-information.md)。  
  
### 執行階段物件模型服務巨集  
  
|||  
|-|-|  
|[DECLARE\_DYNAMIC](../Topic/DECLARE_DYNAMIC.md)|啟用執行階段類別資訊的存取權 \(必須在類別宣告\)。|  
|[DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md)|啟用動態建立和擷取至執行階段類別資訊 \(必須在類別宣告\)。|  
|[DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md)|啟用序列化和擷取至執行階段類別資訊 \(必須在類別宣告\)。|  
|[IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md)|啟用執行階段類別資訊的存取權 \(必須在類別建立\)。|  
|[IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md)|啟用動態建立和擷取至執行階段資訊 \(必須在類別建立\)。|  
|[IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md)|允許序列化和擷取至執行階段類別資訊 \(必須在類別建立\)。|  
|[RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)|傳回對應於名為類別的 `CRuntimeClass` 結構。|  
  
 OLE 通常需要物件的動態建立在執行階段。  例如，一個 OLE 伺服器應用程式必須能夠動態建立 OLE 項目以回應來自用戶端的要求。  同樣地， Automation 伺服器必須能夠建立項目以回應從 Automation 用戶端的要求。  
  
 MFC 程式庫提供特定兩個巨集給 OLE。  
  
### OLE 物件的動態建立  
  
|||  
|-|-|  
|[DECLARE\_OLECREATE](../Topic/DECLARE_OLECREATE.md)|物件可以透過 OLE Automation 建立。|  
|[IMPLEMENT\_OLECREATE](../Topic/IMPLEMENT_OLECREATE.md)|使這個物件是由 OLE 系統建立。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)