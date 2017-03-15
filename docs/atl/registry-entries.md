---
title: "Registry Entries | Microsoft Docs"
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
  - "登錄, application IDs"
  - "登錄, ATL services entries"
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Registry Entries
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DCOM 引入應用程式 ID \(AppIDs\) 的概念，將一個或多個 DCOM 物件的組態選項輸入登錄的集中位置。  您可以指出它的值會指定在名為 AppID AppID 值在物件的 CLSID 底下。  
  
 根據預設，會將 ATL 所產生的服務使用其 CLSID 將 GUID 為其 AppID。  在 `HKEY_CLASSES_ROOT\AppID`之下，您可以指定 DCOM 特定項目。  一開始，有兩個項目:  
  
-   `LocalService`，其值等於服務的名稱。  如果這個值存在，則會使用 \(而非在 CLSID 底下的 `LocalServer32` 索引鍵。  
  
-   `ServiceParameters`，與相等的值。 `–Service`。  這個值指定要傳遞至服務的參數，會在啟動時。  請注意這些參數會傳遞至服務的 `ServiceMain` 函式，而不是 `WinMain`。  
  
 所有 DCOM 服務也需要建立另一個索引鍵。 `HKEY_CLASSES_ROOT\AppID`之下。  因為它包含指回到 AppID 輸入的 AppID 值，這個索引鍵與可執行檔的名稱相等和做為參考。  
  
## 請參閱  
 [服務](../atl/atl-services.md)