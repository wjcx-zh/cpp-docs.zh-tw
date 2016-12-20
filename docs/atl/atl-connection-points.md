---
title: "ATL 連接點 | Microsoft Docs"
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
  - "ATL, 連接點"
  - "連接點 [C++], 關於連接點"
  - "連接, 連接點"
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 連接點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可連接物件是指支援輸出介面的物件。  輸出介面可讓物件與用戶端通訊。  針對每個輸出介面，可連接物件都會公開一個連接點。  每個輸出介面都是由稱為接收 \(sink\) 的物件上的用戶端所實作。  
  
 ![連接點](../atl/media/vc2zw31.png "vc2ZW31")  
  
 每一個連接點皆支援 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318) 介面。  可連接物件會透過 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857) 介面向用戶端公開其連接點。  
  
## 本章節內容  
 [ATL 連接點類別](../atl/atl-connection-point-classes.md)  
 簡短說明支援連接點的 ATL 類別。  
  
 [將連接點加入物件](../atl/adding-connection-points-to-an-object.md)  
 概述用來將連接點加入物件的步驟。  
  
 [ATL 連接點範例](../atl/atl-connection-point-example.md)  
 提供宣告連接點的範例。  
  
## 相關章節  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)