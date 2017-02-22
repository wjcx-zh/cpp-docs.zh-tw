---
title: "CSettingsStoreSP Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSettingsStoreSP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSettingsStoreSP class"
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CSettingsStoreSP Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CSettingsStoreSP` 類別是可用來建立 [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)的執行個體 \(Instance\) 的 Helper 類別。  
  
## 語法  
  
```  
class CSettingsStoreSP  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSettingsStoreSP::CSettingsStoreSP](../Topic/CSettingsStoreSP::CSettingsStoreSP.md)|建構 `CSettingsStoreSP` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSettingsStoreSP::Create](../Topic/CSettingsStoreSP::Create.md)|若要從 `CSettingsStore`衍生類別的執行個體。|  
|[CSettingsStoreSP::SetRuntimeClass](../Topic/CSettingsStoreSP::SetRuntimeClass.md)|設定執行階段類別。  `Create` 方法使用執行階段的類別會決定物件的類別所建立的。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|`m_dwUserData`|在 `CSettingsStoreSP` 物件中儲存的自訂使用者資料。  您可在 `CSettingsStoreSP` 物件之建構函式的這個資料。|  
|`m_pRegistry`|`CSettingsStore`\- `Create` 方法建立的衍生物件。|  
  
## 備註  
 您可以使用 `CSettingsStoreSP` 類別會將所有 MFC 註冊作業重新導向至其他位置，例如 XML 檔或資料庫。  若要執行這項操作，請依照下列步驟執行：  
  
1.  建立類別 \(例如\) `CMyStore`並從 `CSettingsStore`衍生出來。  
  
2.  使用 [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 和 [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md) 巨集以自己的自訂 `CSettingsStore` 類別啟用動態建立。  
  
3.  覆寫虛擬函式並實作自訂類別的 `Read` 和 `Write` 函式。  實作其他功能給預期位置讀取和寫入資料。  
  
4.  在您的應用程式，請呼叫 `CSettingsStoreSP::SetRuntimeClass` 並將指標從類別衍生的 [CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md) 。  
  
 每當這個架構通常會存取登錄，會動態地出現在具現化自訂類別並使用它讀取或寫入資料。  
  
 `CSettingsStoreSP::SetRuntimeClass` 使用全域靜態變數。  因此，只有自訂儲存一次可供使用。  
  
## 需求  
 **標題:** afxsettingsstore.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)