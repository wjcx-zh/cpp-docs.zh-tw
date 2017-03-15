---
title: "網際網路上的非同步 Moniker | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 非同步"
  - "非同步 Moniker [C++]"
  - "下載網際網路資源和非同步 Moniker"
  - "網際網路 [C++], 非同步下載"
  - "MFC [C++], 非同步 Moniker"
  - "最佳化 [C++], 跨網際網路非同步下載"
  - "Web 應用程式 [C++], 非同步"
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 網際網路上的非同步 Moniker
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由於緩慢的網路存取，網際網路需要加入新的方法至應用程式設計。  應用程式應該非同步地執行網路存取，避免讓使用者介面失去作用。  MFC 類別 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) 為下載檔案提供非同步支援。  
  
 有了非同步 Moniker，您可以擴充 COM 應用程式，跨網際網路非同步地下載並提供大型物件的轉換，例如點陣圖和 VRML 物件。  非同步 Moniker 在網際網路啟用要下載的 ActiveX 控制項屬性或檔案中網際網路，而不會封鎖使用者介面的回應。  
  
## 非同步 Moniker 的優點  
 您可以使用非同步 Moniker 進行：  
  
-   下載程式碼和檔案，並且不會封鎖。  
  
-   在 ActiveX 控制項下載屬性，並且不會封鎖。  
  
-   接收下載進度通知。  
  
-   追蹤進度和就緒狀態資訊。  
  
-   提供進度的狀態資訊給使用者。  
  
-   允許使用者隨時取消下載。  
  
## 非同步 Moniker 的 MFC 類別  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) 衍生自 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)，其又是衍生自 [COleStreamFile](../mfc/reference/colestreamfile-class.md)。  `COleStreamFile` 物件表示資料流；`CMonikerFile` 物件使用 `IMoniker` 取得資料，而 `CAsyncMonikerFile` 也是非同步地如此做。  
  
 非同步 Moniekr 主要使用在網際網路可用的應用程式和 ActiveX 控制項，在檔案傳輸期間提供反應靈敏的使用者介面。  一個基本的使用範例是使用 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) 為 ActiveX 控制項提供非同步屬性。  
  
## MFC 類別 ActiveX 控制項的資料路徑  
 MFC 類別 `CDataPathProperty` 和 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) 實作可以非同步載入的 ActiveX 控制項屬性。  非同步屬性在同步初始之後載入。  非同步 ActiveX 控制項重複叫用回呼，在長時間的屬性交換過程中表示新資料的可用性。  
  
 `CDataPathProperty` 是衍生自 `CAsyncMonikerFile`。  `CCachedDataPathProperty` 是衍生自 `CDataPathProperty`。  若要實作您的 ActiveX 控制項的非同步屬性，從 `CDataPathProperty` 或 `CCachedDataPathProperty` 衍生類別，並覆寫 [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) 和您想要接收的其他通知。  
  
#### 若要使用非同步 Moniker 下載檔案  
  
1.  宣告一個會衍生自 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) 的類別。  
  
2.  覆寫 [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) 以顯示資料。  
  
3.  覆寫其他成員函式，包括 [OnProgress](../Topic/CAsyncMonikerFile::OnProgress.md)、[OnStartBinding](../Topic/CAsyncMonikerFile::OnStartBinding.md) 和 [OnStopBinding](../Topic/CAsyncMonikerFile::OnStopBinding.md)。  
  
4.  宣告這個類別的執行個體來開啟 URL。  
  
 如需在 ActiveX 控制項非同步下載的詳細資訊，請參閱 [在網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)。  
  
## 請參閱  
 [MFC 網際網路程式設計工作](../mfc/mfc-internet-programming-tasks.md)   
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)