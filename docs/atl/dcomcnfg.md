---
title: "DCOMCNFG | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DCOMCNFG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DCOM, configuring in ATL"
  - "DCOMCNFG utility"
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# DCOMCNFG
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**DCOMCNFG** 是可讓您設定登錄中的各種 DCOM 特定設定的 Windows NT 4.0 公用程式。  **DCOMCNFG** 視窗有三個頁面上:預設安全性、預設屬性和應用程式。  在 Windows 2000 下第四個頁面上，預設通訊協定，存在。  
  
## 預設安全性頁  
 您可以使用預設安全性頁指定物件的預設使用權限在系統上。  預設安全性頁具有三個部分:存取、啟動及設定。  若要變更區段的預設值，請按一下對應的 **Edit Default** 按鈕。  這些預設安全性設定在 `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`底下之登錄中。  
  
## 預設通訊協定頁面  
 本頁列出組網路通訊協定可供在這部電腦的 DCOM。  這個命令會反映它們所使用的優先權;第一個項目清單具有最高優先權。  通訊協定可從這個頁面加入或刪除。  
  
## 預設屬性頁  
 在預設屬性，如果您想要在其他電腦上的用戶端存取在這部電腦上，網頁的 COM 物件，您必須選取 **Enable Distributed COM on this computer** 核取方塊。  選取這個選項設定 `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` 值組 `Y`。  
  
## 應用程式頁面  
 您變更特定物件的設定與應用程式頁面。  選取應用程式並按一下 \[**屬性**\] 按鈕。  屬性視窗有五個網頁:  
  
-   一般網頁檢查您所使用的應用程式。  
  
-   位置頁可讓您指定應用程式應該在哪裡。執行時，用戶端會在相關的 CLSID 時的 `CoCreateInstance` 。  如果您選取 **Run application on the following computer** 核取方塊並輸入電腦名稱，則 `RemoteServerName` 值加入到該應用程式的 AppID 之下。  **Run application on this computer** 清除核取方塊。 `LocalService` 值重新命名為，並 `_LocalService` ，因此。  
  
-   安全性網頁類似於 **DCOMCNFG** 視窗中的預設安全性\] 頁面，不過，這些設定只會套用至目前的應用程式。  同樣地，設定儲存在該物件的 AppID 之下。  
  
-   識別網頁識別哪一個使用者用來執行應用程式。  
  
-   端點頁列出組通訊協定和端點提供替代的 DCOM 伺服器的用戶端使用。  
  
## 請參閱  
 [服務](../atl/atl-services.md)