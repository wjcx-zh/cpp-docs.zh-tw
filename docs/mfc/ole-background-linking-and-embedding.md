---
title: "OLE 背景：連結與內嵌 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內嵌物件 [C++]"
  - "項目類型"
  - "項目類型, 已定義的"
  - "連結的項目 (OLE) [C++]"
  - "OLE 內嵌項目"
  - "OLE 項目, 類型"
  - "OLE, 連結的項目"
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 背景：連結與內嵌
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用在容器應用程式的貼上命令可以建立內嵌元件或內嵌項目。  內嵌項目的來源資料儲存為包含它的 OLE 文件的一部分。  如此一來，文書處理器文件的文件包含文字也可能包含點陣圖、圖表、公式，或任何其他型別的資料。  
  
 OLE 提供另一種合併來自另一個應用程式的資料:建立連結的元件或連接的項目或連結。  建立連結的項目步驟類似於建立的內嵌項目，不過，您是使用貼上連結命令而非貼上命令。  不同於內嵌元件，連結的元件儲存路徑至原始資料，通常是在個別的檔案中。  
  
 例如，如果文書處理器文件工作並建立連結的項目至陣列報表儲存格，資料連接的項目在原始的報告資料夾中。  文書處理器文件包含指定位置的資訊可以找到項目，也就是，它包含連結至原始的報表資料。  當您按兩下儲存格時，報告應用程式啟動，而原始報告資料從儲存的地方載入。  
  
 每個 OLE 項目，內嵌或連結是否有型別與它以建立自己的應用程式。  例如， Microsoft Paintbrush 繪圖軟體項目是項目的型別，因此， Microsoft Excel 項目是另一個型別。  不過，某些應用程式，可以建立一個以上的項目型別。  例如，可以建立 Microsoft Excel 工作表項目、圖形項目和 macrosheet 項目。  使用類別識別碼或 **CLSID**，這些項目都可以由系統唯一識別。  
  
## 請參閱  
 [OLE 背景](../mfc/ole-background.md)   
 [OLE 背景：容器和伺服器](../mfc/ole-background-containers-and-servers.md)   
 [容器：用戶端項目](../mfc/containers-client-items.md)   
 [伺服器：伺服器項目](../mfc/servers-server-items.md)