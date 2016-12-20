---
title: "CDataPathProperty Class | Microsoft Docs"
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
  - "CDataPathProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 非同步"
  - "asynchronous controls [C++]"
  - "CDataPathProperty class"
  - "OLE 控制項 [C++], 非同步"
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataPathProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作以非同步方式載入的 OLE 控制項屬性。  
  
## 語法  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDataPathProperty::CDataPathProperty](../Topic/CDataPathProperty::CDataPathProperty.md)|建構 `CDataPathProperty` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDataPathProperty::GetControl](../Topic/CDataPathProperty::GetControl.md)|擷取非同步 OLE 控制項與 `CDataPathProperty` 物件。|  
|[CDataPathProperty::GetPath](../Topic/CDataPathProperty::GetPath.md)|擷取屬性的路徑名稱。|  
|[CDataPathProperty::Open](../Topic/CDataPathProperty::Open.md)|啟始非同步屬性的載入關聯的 ActiveX \(OLE\) 控制項。|  
|[CDataPathProperty::ResetData](../Topic/CDataPathProperty::ResetData.md)|呼叫 `CAsyncMonikerFile::OnDataAvailable` 告知容器控制項的屬性已變更。|  
|[CDataPathProperty::SetControl](../Topic/CDataPathProperty::SetControl.md)|設定非同步 ActiveX \(OLE\) 控制項相關聯的屬性。|  
|[CDataPathProperty::SetPath](../Topic/CDataPathProperty::SetPath.md)|設定屬性的路徑名稱。|  
  
## 備註  
 非同步屬性在同步處理初始之後載入。  
  
 類別 `CDataPathProperty`**CAysncMonikerFile**從衍生。  若要實作您的 OLE 控制項的非同步屬性，從 `CDataPathProperty`衍生類別，並覆寫 [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md)。  
  
 如需如何使用非同步標記和 ActiveX 控制項的詳細資訊在網際網路應用程式，請參閱下列文件:  
  
-   [網際網路第一個步驟:ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
-   [網際網路第一個步驟:非同步標記](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [MFC 範例影像](../../top/visual-cpp-samples.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)