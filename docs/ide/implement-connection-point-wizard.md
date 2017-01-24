---
title: "實作連接點精靈 | Microsoft Docs"
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
  - "vc.codewiz.impl.cp.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "實作連接點精靈 [C++]"
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實作連接點精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個精靈可實作 COM 物件的連接點。  可連接物件 \(即來源\) 可以公開本身的介面或任何輸出介面的連接點。  Visual C\+\+ 和 Windows 都提供具有輸出介面的型別程式庫。  每個輸出介面都可由物件上的用戶端 \(也就是接收\) 來實作。  
  
 如需詳細資訊，請參閱 [ATL 連接點](../atl/atl-connection-points.md)。  
  
 **可用的型別程式庫**  
 顯示可用的型別程式庫，其中包含可實作連接點的介面定義。  按一下省略按鈕來找出包含要使用之型別程式庫的檔案。  
  
 **Location**  
 顯示目前在 \[可用的型別程式庫\] 清單中選取的型別程式庫位置。  
  
 **介面**  
 顯示介面，而介面的定義包含在 \[可用的型別程式庫\] 方塊目前所選取的型別程式庫中。  
  
|傳送按鈕|描述|  
|----------|--------|  
|**\>**|將目前在 \[介面\] 清單中選取的介面名稱加入至 \[實作連接點\] 清單。|  
|**\>\>**|將 \[介面\] 清單中所有可用介面名稱加入至 \[實作連接點\] 清單。|  
|**\<**|移除目前在 \[實作連接點\] 清單中選取的介面名稱。|  
|**\<\<**|移除列在 \[實作連接點\] 清單中的所有介面名稱。|  
  
 **實作連接點**  
 顯示介面名稱，當您按一下 \[完成\] 時便會為這些介面實作連接點。  
  
## 請參閱  
 [實作連接點](../ide/implementing-a-connection-point-visual-cpp.md)