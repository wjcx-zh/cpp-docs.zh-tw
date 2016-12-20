---
title: "實作介面精靈 | Microsoft Docs"
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
  - "vc.codewiz.impl.interface.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "實作介面精靈 [C++]"
ms.assetid: 947c329e-0815-4ca7-835e-c41dfeb75f9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實作介面精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個精靈可實作 COM 物件的介面。  許多介面的實作都包含在 Visual Studio 和 Windows 提供的 COM 程式庫中。  當建立了物件的執行個體時，介面實作就和物件產生關聯，同時提供物件所提供的服務。  
  
 如需介面和實作的討論，請參閱 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[介面和介面實作](http://msdn.microsoft.com/library/windows/desktop/ms694356)。  
  
 **實作介面來源**  
 指定建立該介面的型別程式庫位置。  
  
|選項|描述|  
|--------|--------|  
|**專案**|型別程式庫為專案一部分。|  
|**登錄**|型別程式庫已登錄於系統中。  \[可用的型別程式庫\] 中會列出已登錄的型別程式庫|  
|**檔案**|當型別程式庫包含在一個檔案中時便不一定要在系統中登錄，  您必須在 \[位置\] 中提供該檔案的位置|  
  
 **可用的型別程式庫**  
 顯示可用的型別程式庫，其中包含可實作的介面定義。  如果您按一下 \[實作介面來源\] 下的 \[檔案\]，便無法變更這個方塊。  
  
 **Location**  
 顯示目前在 \[可用的型別程式庫\] 清單中選取的型別程式庫位置。  如果您選取了 \[實作介面來源\] 下的 \[檔案\]，請按一下省略按鈕，以找尋包含要使用之型別程式庫的檔案。  
  
 **介面**  
 顯示介面，而介面的定義包含在 \[可用的型別程式庫\] 方塊目前所選取的型別程式庫中。  
  
> [!NOTE]
>  和所選取物件已實作之介面同名的介面不會顯示在 \[介面\] 方塊中。  
  
|傳送按鈕|描述|  
|----------|--------|  
|**\>**|將目前在 \[介面\] 清單中選取的介面名稱加入至 \[實作介面\] 清單。|  
|**\>\>**|將 \[介面\] 清單中所有可用介面名稱加入至 \[實作介面\] 清單。|  
|**\<**|移除目前在 \[實作介面\] 清單中選取的介面名稱。|  
|**\<\<**|移除列在 \[實作介面\] 清單中的所有介面名稱。|  
  
 **實作介面**  
 顯示要在物件上實作的已選取介面名稱。  
  
> [!NOTE]
>  如果包含一個以上衍生自 `IDispatch` 的介面，或是如果您嘗試實作的介面是衍生自已經在您的類別上的其他介面，則必須清楚區分 COM\_MAP 項目。  如需詳細資訊，請參閱 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md)。  
  
## 請參閱  
 [實作介面](../ide/implementing-an-interface-visual-cpp.md)