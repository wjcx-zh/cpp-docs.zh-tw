---
title: "ASP, ATL Active Server Page 元件精靈 | Microsoft Docs"
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
  - "vc.codewiz.class.atl.asp.asp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL Active Server Page 元件精靈, ASP"
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ASP, ATL Active Server Page 元件精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用此 ATL Active Server Page 元件精靈頁面來為與您 ASP 元件相關的處理資訊和狀態指定選擇性的設定。  
  
 **選擇性方法**  
 將選擇性 ASP 方法 **OnStartPage** 和 **OnEndPage** 加入至您的物件。  這個選項必須選取來設定任何 Active Server Pages 內建 \(Intrinsic\) 物件。  依預設是選取的。  
  
-   **OnStartPage\/OnEndPage** 指令碼第一次嘗試存取物件時會呼叫 [OnStartPage](https://msdn.microsoft.com/en-us/library/ms691624.aspx)。  當物件完成處理指令碼時則會呼叫 **OnEndPage**。  
  
 **內建物件**  
 您必須選取 **OnStartPage\/OnEndPage** 選項來設定任何 ASP 內建物件。  
  
|選項|描述|  
|--------|--------|  
|**要求**|提供 Active Server Pages 內建 **Request** 物件的存取。  Request 物件是用來傳遞 HTTP 要求。|  
|**回應**|提供 Active Server Pages 內建 **Response** 物件的存取。  為回應要求，Response 物件會將資訊傳送至瀏覽器以顯示給使用者看。|  
|**工作階段**|提供 Active Server Pages 內建 **Session** 物件的存取。  **Session** 物件維護目前使用者工作階段 \(Session\) 的資訊，包括儲存和擷取狀態資訊。|  
|**應用程式**|提供對 Active Server Pages 內建 **Application** 物件的存取。  **Application** 物件管理多個 ASP 物件之間共用的狀態。|  
|**伺服器**|提供 Active Server Pages 內建 **Server** 物件的存取。  **Server** 物件允許您建立其他 ASP 物件。|  
  
## 請參閱  
 [ATL Active Server Page 元件精靈](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page Component](../../atl/reference/adding-an-atl-active-server-page-component.md)