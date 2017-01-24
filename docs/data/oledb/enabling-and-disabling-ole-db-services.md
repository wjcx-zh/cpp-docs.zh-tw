---
title: "啟用和停用 OLE DB 服務 | Microsoft Docs"
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
  - "OLE DB 服務 [OLE DB], 啟用和停用"
  - "服務提供者 [OLE DB]"
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 啟用和停用 OLE DB 服務
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 服務元件管理員會比較消費者所指定的屬性和提供者所支援的屬性，以決定是否叫用 \(Invoke\) 個別的服務元件來滿足消費者所要求的擴充功能。  例如，如果應用程式要求一個可捲動的指標，而提供者僅支援只能順向的指標，服務元件管理員就會叫用 Client Cursor Engine 服務元件，來提供可捲動的功能。  如果應用程式依賴提供者的資料列集預設提供的擴充功能，而應用程式並未明確地設定屬性來要求該功能，此功能可能不會出現在 Client Cursor Engine 傳回的資料列集內。  若要互動式操作，應用程式應在需要的地方設定屬性，以明確地要求擴充的功能。  
  
 在某些情況下，您可能需要停用個別的 OLE DB 服務，以便妥善使用已擁有提供者特性的現有應用程式。  OLE DB 服務提供了可停用個別服務或所有服務的功能，不論是在個別連接的基礎上，或針對使用單一提供者的所有應用程式。  
  
## 請參閱  
 [OLE DB 資源集中化和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)