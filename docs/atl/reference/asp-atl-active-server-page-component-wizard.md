---
title: "ASP，ATL Active Server Page 元件精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.asp.asp
dev_langs: C++
helpviewer_keywords: ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69d3837cc0996c0e0e0784214cfbfa6744afbf94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, ATL Active Server Page 元件精靈
使用 ATL Active Server Page 元件精靈的這個頁面可指定選擇性設定處理資訊和相關 ASP 元件的狀態。  
  
 **選擇性方法**  
 會加入選擇性的 ASP 方法， **OnStartPage**和**OnEndPage**，對您物件。 若要設定的任何 Active Server Pages 內建函式物件，就必須選取此選項。 根據預設，它會選取。  
  
-   **OnStartPage/OnEndPage** [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx)稱為第一次指令碼嘗試存取的物件。 **OnEndPage**物件完成時，會呼叫處理指令碼。  
  
 **內建物件**  
 您必須選取**OnStartPage/OnEndPage**選項可用來設定任何 ASP 內建物件。  
  
|選項|描述|  
|------------|-----------------|  
|**要求**|Active Server Pages 內建函式提供存取**要求**物件。 要求物件用來將 HTTP 要求。|  
|**回應**|Active Server Pages 內建函式提供存取**回應**物件。 要求的回應，回應物件會將資訊傳送到瀏覽器顯示給使用者。|  
|**工作階段**|Active Server Pages 內建函式提供存取**工作階段**物件。 **工作階段**物件會維護目前使用者工作階段，包括儲存及擷取狀態資訊的相關資訊。|  
|**應用程式**|Active Server Pages 內建函式提供存取**應用程式**物件。 **應用程式**物件管理跨多個 ASP 物件共用的狀態。|  
|**伺服器**|Active Server Pages 內建函式提供存取**伺服器**物件。 **伺服器**物件可讓您建立其他 ASP 物件。|  
  
## <a name="see-also"></a>請參閱  
 [ATL Active Server Page 元件精靈](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL Active Server Page 元件](../../atl/reference/adding-an-atl-active-server-page-component.md)

