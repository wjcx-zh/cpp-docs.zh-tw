---
title: "Benefits and Tradeoffs of the Method Used to Link to the CRT | Microsoft Docs"
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
  - "_ATL_MIN_CRT 巨集"
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Benefits and Tradeoffs of the Method Used to Link to the CRT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的專案可以使用 CRT 動態或靜態連結。  概略說明資料表優點和交易中使用之方法的相關的選項。  
  
|方法|優點|交易|  
|--------|--------|--------|  
|靜態連結至 CRT<br /><br /> \(**執行階段程式庫** 設為 **Single\-threaded**\)|CRT DLL 在影像上執行的系統不需要。|如需啟動程式碼 25K 加入至影像，大幅增加控制項的大小。|  
|動態連結至 CRT<br /><br /> \(**執行階段程式庫** 設為 **多執行緒**\)|您的影像不需要 CRT 啟始程式碼，因此，它會較小。|CRT DLL 必須在執行影像的系統。|  
  
 本主題討論如何 [連結至您的 ATL 專案的 CRT](../atl/linking-to-the-crt-in-your-atl-project.md) 替代 CRT 之連結的方式提供。  
  
## 請參閱  
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../atl/programming-with-atl-and-c-run-time-code.md)   
 [執行階段程式庫行為](../build/run-time-library-behavior.md)   
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)