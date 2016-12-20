---
title: "ATL OLE DB 提供者精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.provider.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL OLE DB 提供者精靈"
  - "ATL 專案, 加入 ATL OLE DB 提供者"
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL OLE DB 提供者精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個精靈會建立組成 OLE DB 提供者的類別。  
  
## 備註  
 從 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 開始，此精靈產生的註冊指令碼將會在 **HKEY\_CURRENT\_USER** 下 \(而非 **HKEY\_LOCAL\_MACHINE** 下\) 註冊它的 COM 元件。  若要修改此行為，請設定 \[ATL 精靈\] 的 \[**登錄所有使用者的元件**\] 選項。  
  
 下表說明 \[ATL OLE DB 提供者精靈\] 中的選項：  
  
 **簡短名稱**  
 請輸入要建立之提供者的簡短名稱，  精靈中的其他編輯方塊會依據您在此處輸入的名稱自動填入。  您可以視需要編輯其他名稱方塊。  
  
 **Coclass**  
 Coclass 的名稱，  ProgID 名稱會變更以符合此名稱。  
  
 **屬性化**  
 這個選項指定精靈是使用屬性 \(Attribute\) 或是樣板宣告來建立提供者類別。  當您選取這個選項時，精靈會使用屬性而不是樣板宣告 \(如果您建立屬性化專案，則這是預設選項\)。  當您清除這個選項時，精靈會使用樣板宣告而不是屬性 \(如果您建立非屬性化專案，則這是預設選項\)。  
  
 如果您在建立非屬性化專案時選取這個選項，精靈會警告您專案將轉換為屬性化專案並詢問您是否要繼續。  
  
 **ProgID**  
 ProgID 或程式設計識別項 \(Programmatic ID\) 是您應用程式可使用的文字字串，而不是 GUID。  ProgID 名稱的格式為 *Projectname*.*Coclassname*。  
  
 **版本**  
 提供者的版本號碼。  預設值為 1。  
  
 **資料來源類別**  
 資料來源類別的名稱，格式為 C`Shortname`Source。  
  
 **資料來源 .h 檔**  
 資料來源類別的標頭檔。  您可以編輯此檔案的名稱或選取現有的標頭檔。  
  
 **工作階段類別**  
 工作階段類別的名稱，格式為 C`Shortname`Session。  
  
 **工作階段 .h 檔**  
 工作階段類別的標頭檔。  您可以編輯此檔案的名稱或選取現有的標頭檔。  
  
 **命令類別**  
 命令類別的名稱，格式為 C`Shortname`Command。  
  
 **命令 .h 檔**  
 命令類別的標頭檔。  此檔案的名稱是依照資料列集 \(RowSet\) 標頭檔的名稱而定，不可編輯此檔案名稱。  
  
 **資料列集類別**  
 資料列集類別的名稱，格式為 C`Shortname`Rowset。  
  
 **資料列集 .h 檔**  
 資料列集類別的標頭檔。  您可以編輯此檔案的名稱或選取現有的標頭檔。  
  
 **資料列集 .cpp 檔**  
 提供者的實作檔。  您可以編輯此檔案的名稱或選取現有的實作檔。  
  
## 請參閱  
 [ATL OLE DB Provider](../../atl/reference/adding-an-atl-ole-db-provider.md)