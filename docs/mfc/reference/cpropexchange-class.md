---
title: "CPropExchange Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPropExchange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項 [MFC], OLE"
  - "CPropExchange 類別"
  - "OLE 控制項, 保存性"
ms.assetid: ed872180-e770-4942-892a-92139d501fab
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPropExchange Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支援永續性實作自己的 OLE 控制項的。  
  
## 語法  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPropExchange::ExchangeBlobProp](../Topic/CPropExchange::ExchangeBlobProp.md)|交換二進位大型物件 \(BLOB\) 的屬性。|  
|[CPropExchange::ExchangeFontProp](../Topic/CPropExchange::ExchangeFontProp.md)|交換的字型屬性。|  
|[CPropExchange::ExchangePersistentProp](../Topic/CPropExchange::ExchangePersistentProp.md)|在控制項和檔案之間的屬性。|  
|[CPropExchange::ExchangeProp](../Topic/CPropExchange::ExchangeProp.md)|交換任何內建的型別屬性。|  
|[CPropExchange::ExchangeVersion](../Topic/CPropExchange::ExchangeVersion.md)|交換 OLE 控制項的版本號碼。|  
|[CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md)|擷取 OLE 控制項的版本號碼。|  
|[CPropExchange::IsAsynchronous](../Topic/CPropExchange::IsAsynchronous.md)|判斷屬性切換是否完成非同步。|  
|[CPropExchange::IsLoading](../Topic/CPropExchange::IsLoading.md)|指示屬性是否載入控制項或其儲存。|  
  
## 備註  
 `CPropExchange` 不具有基底類別。  
  
 建立屬性交換內容和方向。  
  
 保存為其屬性，通常表示的控制項狀態資訊交換，在控制項和媒體之間。  
  
 架構會從 `CPropExchange` 衍生物件，當通知時 OLE 控制項的屬性 \(Property\) 會從載入或儲存至持續性儲存體。  
  
 架構會將指標對控制項的 `DoPropExchange` 函式的這個 `CPropExchange` 物件。  如果您使用精靈來建立起始為您的控制項，控制項的 `DoPropExchange` 函式呼叫 `COleControl::DoPropExchange`檔案。  基底類別版本交換控制項共用的屬性，您可以修改您的衍生類別版本交換已加入至控制項的屬性。  
  
 `CPropExchange` 可用來將控制項的屬性或初始化控制項的屬性是在控制項的載入或建立。  `CPropExchange` 的 `ExchangeProp` 和 `ExchangeFontProp` 成員函式可以將屬性設定為、從不同媒體載入它們。  
  
 如需使用 `CPropExchange`的詳細資訊，請參閱本文 [MFC ActiveX 控制項:屬性頁](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## 繼承階層架構  
 `CPropExchange`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)