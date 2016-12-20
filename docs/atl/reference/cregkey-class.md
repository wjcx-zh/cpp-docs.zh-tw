---
title: "CRegKey Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRegKey"
  - "ATL::CRegKey"
  - "ATL.CRegKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 登錄"
  - "CRegKey class"
  - "登錄, 刪除索引鍵"
  - "登錄, 刪除值"
  - "登錄, 寫入至"
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRegKey Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供對作業系統中登錄的輸入的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CRegKey  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRegKey::CRegKey](../Topic/CRegKey::CRegKey.md)|建構函式。|  
|[CRegKey::~CRegKey](../Topic/CRegKey::~CRegKey.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRegKey::Attach](../Topic/CRegKey::Attach.md)|呼叫這個方法要附加至 `CRegKey` 物件可透過將 [m\_hKey](../Topic/CRegKey::m_hKey.md) 成員的控制代碼。 `hKey`。|  
|[CRegKey::Close](../Topic/CRegKey::Close.md)|呼叫這個方法會釋放 [m\_hKey](../Topic/CRegKey::m_hKey.md) 成員控制代碼並將其設為 null。|  
|[CRegKey::Create](../Topic/CRegKey::Create.md)|如果不存在則為， `hKeyParent`子機碼呼叫這個方法會為指定的索引鍵。|  
|[CRegKey::DeleteSubKey](../Topic/CRegKey::DeleteSubKey.md)|呼叫這個方法會從登錄中移除指定的索引鍵。|  
|[CRegKey::DeleteValue](../Topic/CRegKey::DeleteValue.md)|呼叫這個方法會從移除 [m\_hKey](../Topic/CRegKey::m_hKey.md)值欄位。|  
|[CRegKey::Detach](../Topic/CRegKey::Detach.md)|呼叫這個方法中斷連結 `CRegKey` 物件的 [m\_hKey](../Topic/CRegKey::m_hKey.md) 成員控制代碼和集合 `m_hKey` 為 NULL。|  
|[CRegKey::EnumKey](../Topic/CRegKey::EnumKey.md)|呼叫這個方法會列舉開啟登錄機碼的子機碼。|  
|[CRegKey::Flush](../Topic/CRegKey::Flush.md)|呼叫這個方法可將所有開啟登錄機碼的屬性寫入登錄中。|  
|[CRegKey::GetKeySecurity](../Topic/CRegKey::GetKeySecurity.md)|呼叫這個方法會擷取保護開啟登錄機碼的安全性描述元的複本。|  
|[CRegKey::NotifyChangeKeyValue](../Topic/CRegKey::NotifyChangeKeyValue.md)|這個方法會告知變更呼叫端存取開啟登錄機碼的屬性或內容。|  
|[CRegKey::Open](../Topic/CRegKey::Open.md)|呼叫這個方法會開啟指定的索引鍵和 [m\_hKey](../Topic/CRegKey::m_hKey.md) 集合加入至這個金鑰控制代碼。|  
|[CRegKey::QueryBinaryValue](../Topic/CRegKey::QueryBinaryValue.md)|呼叫這個方法會擷取某個值名稱的二進位資料。|  
|[CRegKey::QueryDWORDValue](../Topic/CRegKey::QueryDWORDValue.md)|呼叫這個方法會擷取 DWORD 資料為指定的值名稱。|  
|[CRegKey::QueryGUIDValue](../Topic/CRegKey::QueryGUIDValue.md)|呼叫這個方法會擷取 GUID 資料為指定的值名稱。|  
|[CRegKey::QueryMultiStringValue](../Topic/CRegKey::QueryMultiStringValue.md)|呼叫這個方法會擷取 multistring 資料的值名稱。|  
|[CRegKey::QueryQWORDValue](../Topic/CRegKey::QueryQWORDValue.md)|呼叫這個方法會擷取 QWORD 資料為指定的值名稱。|  
|[CRegKey::QueryStringValue](../Topic/CRegKey::QueryStringValue.md)|呼叫這個方法會擷取資料行的資料。指定名稱。|  
|[CRegKey::QueryValue](../Topic/CRegKey::QueryValue.md)|呼叫這個方法會擷取資料。 [m\_hKey](../Topic/CRegKey::m_hKey.md)指定欄位。  這個方法舊版不再支援和標記為 **ATL\_DEPRECATED**。|  
|[CRegKey::RecurseDeleteKey](../Topic/CRegKey::RecurseDeleteKey.md)|呼叫這個方法會從登錄中移除指定的索引鍵和明確移除所有子機碼。|  
|[CRegKey::SetBinaryValue](../Topic/CRegKey::SetBinaryValue.md)|呼叫這個方法會設定登錄機碼的二進位值。|  
|[CRegKey::SetDWORDValue](../Topic/CRegKey::SetDWORDValue.md)|呼叫這個方法會設定登錄機碼的 DWORD 值。|  
|[CRegKey::SetGUIDValue](../Topic/CRegKey::SetGUIDValue.md)|呼叫這個方法會設定登錄機碼的 GUID 值。|  
|[CRegKey::SetKeySecurity](../Topic/CRegKey::SetKeySecurity.md)|呼叫這個方法會設定登錄機碼的安全性。|  
|[CRegKey::SetKeyValue](../Topic/CRegKey::SetKeyValue.md)|呼叫這個方法會在指定的指定索引鍵欄位儲存資料。|  
|[CRegKey::SetMultiStringValue](../Topic/CRegKey::SetMultiStringValue.md)|呼叫這個方法會設定登錄機碼的 multistring 的值。|  
|[CRegKey::SetQWORDValue](../Topic/CRegKey::SetQWORDValue.md)|呼叫這個方法會設定登錄機碼的 QWORD 值。|  
|[CRegKey::SetStringValue](../Topic/CRegKey::SetStringValue.md)|呼叫這個方法會設定登錄機碼的字串值。|  
|[CRegKey::SetValue](../Topic/CRegKey::SetValue.md)|呼叫這個方法會在指定的 [m\_hKey](../Topic/CRegKey::m_hKey.md)欄位來儲存資料。  這個方法舊版不再支援和標記為 **ATL\_DEPRECATED**。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CRegKey::operator HKEY](../Topic/CRegKey::operator%20HKEY.md)|要轉換成的 `CRegKey` 物件。|  
|[CRegKey::operator \=](../Topic/CRegKey::operator%20=.md)|指派運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CRegKey::m\_hKey](../Topic/CRegKey::m_hKey.md)|包含登錄機碼的控制代碼與 `CRegKey` 物件。|  
|[CRegKey::m\_pTM](../Topic/CRegKey::m_pTM.md)|為 `CAtlTransactionManager` 物件的指標。|  
  
## 備註  
 `CRegKey` 提供建立和刪除機碼和值提供方法在系統登錄。  註冊包含安裝特定一組系統元件的定義，例如軟體版本號碼、安裝的硬體邏輯與實體對應和 COM 物件。  
  
 `CRegKey` 提供程式設計介面寫入系統登錄指定的電腦。  例如，開啟特定登錄機碼，呼叫 `CRegKey::Open`。  擷取或修改資料值、呼叫 `CRegKey::QueryValue` 或 `CRegKey::SetValue`，名稱分別為、和。  若要關閉機碼，請呼叫 `CRegKey::Close`。  
  
 在您關閉機碼時，它的登錄資料寫入硬碟時寫入 \(清除\)。  這個程序可能需要幾秒鐘。  如果您的應用程式必須寫入硬碟時明確寫入登錄資料，您可以呼叫 [RegFlushKey](http://msdn.microsoft.com/library/windows/desktop/ms724867) Win32 函式。  不過， **RegFlushKey** 使用許多系統資源，且應呼叫，只在絕對需要。  
  
> [!IMPORTANT]
>  允許呼叫端指定登錄位置的所有方法都可能會無法信任的資料。  使用 [RegQueryValueEx](http://msdn.microsoft.com/library/windows/desktop/ms724911) 的方法應該考慮這個函式不會明確處理是以 null 結束的字串。  應該檢查兩個條件由呼叫程式碼。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [DCOM 範例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Registry Overview](http://msdn.microsoft.com/library/windows/desktop/ms724871)   
 [Registry Functions](http://msdn.microsoft.com/library/windows/desktop/ms724875)   
 [Registry Value Types](http://msdn.microsoft.com/library/windows/desktop/ms724884)