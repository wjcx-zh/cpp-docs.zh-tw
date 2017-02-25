---
title: "選項, ATL 簡單物件精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.simple.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 簡單物件精靈, 選項"
ms.assetid: 125fe179-942d-4181-8b82-33e92e1fd779
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 選項, ATL 簡單物件精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用此 ATL 簡單物件精靈頁面來設計物件以增加效率和錯誤支援。  
  
 如需 ATL 專案和 ATL COM 類別的詳細資訊，請參閱 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)。  
  
 **執行緒模型**  
 指示管理執行緒的方法。  專案預設使用 **Apartment** 執行緒。  
  
 如需詳細資訊，請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。  
  
|選項|描述|  
|--------|--------|  
|`Single`|指定物件都必須在主要 COM 執行緒中執行。  如需詳細資訊，請參閱[單一執行緒 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112) 和 [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)。|  
|**Apartment**|指定物件使用 Apartment 執行緒。  與單一執行緒 Apartment 相同。  在物件存留期間會為 Apartment 執行緒元件的每個物件指派 Apartment 給其執行緒；不過，多個物件可使用多個執行緒。  每個 Apartment 會與特定執行緒建立關聯，並具有 Windows 訊息幫浦 \(Message Pump\) \(預設值\)。<br /><br /> 如需詳細資訊，請參閱[單一執行緒 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112)。|  
|**Both**|根據建立物件的執行緒類型來指定物件可使用 Apartment 或無限制執行緒 \(Free Threading\)。|  
|**Free**|指定物件使用無限制執行緒。  無限制執行緒和多執行緒 Apartment 模型 \(Multithreaded Apartment Model，MTA\) 相同。  如需詳細資訊，請參閱[多執行緒 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms693421)。|  
|**Neutral** \(僅適用 Windows 2000\)|指定物件必須依照多執行緒 Apartment 的方針，但它可在任何類型的執行緒上執行。|  
  
 **Aggregation**  
 指出物件是否使用[彙總](http://msdn.microsoft.com/library/windows/desktop/ms686558)。  彙總物件會選擇哪些是要公開 \(Expose\) 給用戶端的介面，而這些介面的公開方式就像是彙總物件實作它們一般。  彙總物件的用戶端只與彙總物件通訊。  
  
|選項|描述|  
|--------|--------|  
|是|指定物件可彙總。  預設值。|  
|否|指定物件不可彙總。|  
|Only|指定物件必須彙總。|  
  
 **介面**  
 指示物件支援的介面類型。  物件預設支援雙重介面。  
  
|選項|描述|  
|--------|--------|  
|**雙重**|指定物件支援雙重介面 \(其 vtable 具有自訂介面功能以及晚期繫結 \(Late Binding\) `IDispatch` 方法\)。  允許 COM 用戶端和 [Automation 控制程式](../../mfc/automation-clients.md)存取物件。  預設值。|  
|**Custom**|指定物件支援自訂介面 \(其 vtable 具有自訂介面函式\)。  自訂介面比雙重介面的速度快，特別是在跨處理序 \(Process\) 界限的時候。<br /><br /> -   **Automation compatible** 允許 Automation 控制程式存取具有自訂介面支援的物件。|  
  
 **支援**  
 指示物件的其他支援。  
  
|選項|描述|  
|--------|--------|  
|**ISupportErrorInfo**|建立 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 介面的支援，使物件能夠將錯誤資訊傳回用戶端。|  
|**連接點**|透過從 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) 衍生物件類別來為您的物件啟用連接點 \(Connection Point\)。|  
|**無限制執行緒封送處理器**|建立無限制執行緒封送處理器 \(Free Threaded Marshaler\) 物件來在相同處理序中的執行緒之間有效地封送處理介面指標。  可讓指定 **Both** 為執行緒模型的物件使用。|  
|**IObjectWithSite \(IE 物件支援\)**|實作 [IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)，它提供了簡易的方法來支援容器中物件與其站台之間的通訊。|  
  
## 請參閱  
 [ATL 簡單物件精靈](../../atl/reference/atl-simple-object-wizard.md)   
 [ATL Simple Object](../../atl/reference/adding-an-atl-simple-object.md)   
 [同處理序執行緒問題](http://msdn.microsoft.com/library/windows/desktop/ms687205)