---
title: "OLE DB 應用程式的資源集中化 | Microsoft Docs"
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
  - "OLE DB 提供者, 資源集中化"
  - "OLE DB 服務 [OLE DB], 資源集中化"
  - "OLE DB, 資源集中化"
  - "資源集中化 [OLE DB], 服務"
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE DB 應用程式的資源集中化
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要在應用程式中運用共用，您必須確定 OLE DB 服務是透過 **IDataInitialize** 或 **IDBPromptInitialize** 取得資料來源進行叫用 \(Invoke\)。  如果您是根據提供者的 CLSID 直接使用 `CoCreateInstance` 來叫用提供者，便不會叫用任何的 OLE DB 服務。  
  
 只要仍在參照 **IDataInitialize** 或 **IDBPromptInitialize**，或有一個連接正在使用中，OLE DB 服務就會維持連接資料來源的集區。  集區也會在 COM\+ 1.0 服務或網際網路資訊服務 \(IIS\) 環境中自動維持。  如果您的應用程式將在 COM\+ 1.0 Services 或 IIS 的環境外運用共用，您應保持 **IDataInitialize** 或 **IDBPromptInitialize** 的參考，或至少維持一個連接。  若要確定上次應用程式釋放連接時不會毀棄集區，請在應用程式的存留期 \(Lifetime\) 內保持參考，或維持連接。  
  
 OLE DB 服務會辨認集區，此集區在呼叫 `Initialize` 時會繪製連接。  從集區繪製一個連接之後，此連接便無法移到不同的集區。  因此，請避免在應用程式內進行會變更初始化資訊的工作，例如在呼叫 `Initialize` 之前，針對提供者專用介面呼叫 `UnInitialize` 或呼叫 `QueryInterface`。  此外，將不會共用 **DBPROMPT\_NOPROMPT** 以外的提示值所建立的連接。  不過，經由提示從建立連接所擷取到的初始化字串可用來將其他的共用連結建立到相同的資料來源。  
  
 有些提供者必須替每個工作階段 \(Session\) 建立個別連接。  這些其他的連接都必須登記於不同的散發交易內，若是存在的話。  OLE DB 服務會針對每個資料來源快取和重複使用工作階段，但如果應用程式同時從單一資料來源中要求一個以上的工作階段，提供者可能不再建立額外的連接以及進行未共用的額外交易登記。  事實上替共用環境中的每個工作階段建立個別的資料來源，比從單一資料來源建立多重工作階段更有效率。  
  
 最後，因為 ADO 會自動使用 OLE DB 服務，您可使用 ADO 來建立連接，共用和登記都會自動發生。  
  
## 請參閱  
 [OLE DB 資源集中化和服務](../../data/oledb/ole-db-resource-pooling-and-services.md)