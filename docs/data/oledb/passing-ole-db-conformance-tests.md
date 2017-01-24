---
title: "通過 OLE DB 一致性測試 | Microsoft Docs"
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
  - "一致性測試"
  - "一致性測試 [OLE DB]"
  - "OLE DB 提供者, 測試"
  - "測試提供者"
  - "測試, OLE DB 提供者"
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 通過 OLE DB 一致性測試
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為了使提供者更為一致，Data Access SDK 提供了一組 OLE DB 一致性測試。  這些測試會檢查提供者的各個層面，並給予提供者函式可如預期運作的合理保證。  您可在 Microsoft Data Access SDK 上找到 OLE DB 的一致性測試。  本章節內容的重點在於應執行步驟來通過一致性測試。  如需執行 OLE DB 一致性測試的詳細資訊，請參閱 SDK。  
  
## 執行一致性測試  
 在 Visual C\+\+ 6.0 中，OLE DB 提供者樣板會加入許多攔截函式，以便檢查數值和屬性。  大多數函式都是為了回應一致性測試而加入的。  
  
> [!NOTE]
>  您需要加入數個驗證函式，提供者才能通過 OLE DB 的一致性測試。  
  
 這個提供者需要兩個驗證常式。  第一個常式 \-\- `CRowsetImpl::ValidateCommandID`，是資料列集類別的一部分。  它會在建立資料列集過程中由提供者樣板呼叫。  範例將使用這個常式來告知消費者它並不支援索引。  第一個呼叫是 `CRowsetImpl::ValidateCommandID` \(請注意，提供者將使用[提供者書籤支援](../../data/oledb/provider-support-for-bookmarks.md)中為 `CMyProviderRowset` 加入至介面對應內的 **\_RowsetBaseClass** typedef，因此您不需輸入這麼長的樣板引數程式碼列\)。  接著，如果索引參數不是 **NULL**，便會傳回 **DB\_E\_NOINDEX** \(這代表消費者想要在這些資料上使用索引\)。  如需命令 ID 的詳細資訊，請檢閱 OLE DB 規格，並尋找 **IOpenRowset::OpenRowset**。  
  
 下列程式碼為 **ValidateCommandID** 驗證常式：  
  
```  
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)  
{  
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);  
   if (hr != S_OK)  
      return hr;  
  
   if (pIndexID != NULL)  
      return DB_E_NOINDEX;    // Doesn't support indexes  
  
   return S_OK;  
}  
```  
  
 每當某人變更 **DBPROPSET\_ROWSET** 群組上的屬性時，提供者樣板就會呼叫 `OnPropertyChanged` 方法。  如果您想要處理其他群組的屬性，可將它們加入至適當物件 \(也就是說，**DBPROPSET\_SESSION** 檢查會放入 `CMyProviderSession` 類別內\)。  
  
 程式碼會先檢查屬性是否連結至另一個屬性。  如果屬性被鏈結，就會將 **DBPROP\_BOOKMARKS** 屬性設成 True。  OLE DB 規格的＜附錄 C＞包含了屬性的資訊。  這個資訊也會告訴您該屬性是否鏈結至另一個屬性。  
  
 您可能也希望將 `IsValidValue` 常式加入至程式碼。  在嘗試設定屬性時，樣板將呼叫 `IsValidValue`。  如果需要其他處理，您可以在設定屬性值時覆寫這個方法。  您可為每個屬性集使用其中一種方法。  
  
## 執行緒問題  
 預設情況下，ATL OLE DB 提供者精靈中的 OLE DB 提供者精靈將產生提供者的程式碼，以便於 Apartment Model 內執行。  如果您嘗試以一致性測試來執行此程式碼，一開始就會失敗。  這是因為用來執行 OLE DB 一致性測試的工具 Ltm.exe 將預設成無限制執行緒 \(Free Thread\)。  OLE DB 提供者精靈程式碼會考慮效能和簡易使用因素，將此預設成 Apartment Model。  
  
 若要修正這個問題，您可以變更 LTM 或變更提供者。  
  
#### 若要變更 LTM 執行於 Apartment 執行緒模式  
  
1.  在 LTM 主功能表內按一下 \[工具\]，然後按一下 \[**選項**\]。  
  
2.  在 \[一般\] 標籤內，將執行緒模型從 \[無限制執行緒\] 變更為 \[Apartment 執行緒\]。  
  
 若要變更提供者執行於無限制執行緒模式中：  
  
-   在提供者專案內，搜尋所有的 `CComSingleThreadModel` 執行個體，將其取代成 `CComMultiThreadModel`，它應該會位於您的資料來源、工作階段 \(Session\) 和資料列集標頭內。  
  
-   在 .rgs 檔內，將執行緒模型從 \[Apartment\] 變更成 \[Both\]。  
  
-   依照正確的程式設計規則來撰寫無限制的執行緒程式 \(也就是鎖定於寫入時\)。  
  
## 請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)