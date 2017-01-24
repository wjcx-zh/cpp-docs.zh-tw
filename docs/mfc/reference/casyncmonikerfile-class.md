---
title: "CAsyncMonikerFile Class | Microsoft Docs"
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
  - "CAsyncMonikerFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 非同步"
  - "asynchronous controls [C++]"
  - "CAsyncMonikerFile class"
  - "IMoniker interface, 繫結"
  - "monikers [C++], MFC"
  - "OLE 控制項 [C++], 非同步"
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAsyncMonikerFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供功能給在 ActiveX 控制項 \(先前稱為 OLE 控制項\) 的非同步標記的使用。  
  
## 語法  
  
```  
class CAsyncMonikerFile : public CMonikerFile  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncMonikerFile::CAsyncMonikerFile](../Topic/CAsyncMonikerFile::CAsyncMonikerFile.md)|建構 `CAsyncMonikerFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncMonikerFile::Close](../Topic/CAsyncMonikerFile::Close.md)|關閉並釋放所有資源。|  
|[CAsyncMonikerFile::GetBinding](../Topic/CAsyncMonikerFile::GetBinding.md)|擷取指標非同步傳輸繫結。|  
|[CAsyncMonikerFile::GetFormatEtc](../Topic/CAsyncMonikerFile::GetFormatEtc.md)|擷取資料的格式在資料流中。|  
|[CAsyncMonikerFile::Open](../Topic/CAsyncMonikerFile::Open.md)|開啟檔案以非同步方式。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](../Topic/CAsyncMonikerFile::CreateBindStatusCallback.md)|建立 COM 物件實作 `IBindStatusCallback`。|  
|[CAsyncMonikerFile::GetBindInfo](../Topic/CAsyncMonikerFile::GetBindInfo.md)|呼叫由 OLE 系統程式庫所需的所建立的繫結型別的資訊。|  
|[CAsyncMonikerFile::GetPriority](../Topic/CAsyncMonikerFile::GetPriority.md)|呼叫由 OLE 系統程式庫取得繫結的優先權。|  
|[CAsyncMonikerFile::OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md)|會提供資料，則它會變成可供用戶端在非同步繫結作業期間。|  
|[CAsyncMonikerFile::OnLowResource](../Topic/CAsyncMonikerFile::OnLowResource.md)|呼叫時，資源不足。|  
|[CAsyncMonikerFile::OnProgress](../Topic/CAsyncMonikerFile::OnProgress.md)|呼叫表示資料下載程序的進度。|  
|[CAsyncMonikerFile::OnStartBinding](../Topic/CAsyncMonikerFile::OnStartBinding.md)|呼叫，在繫結時啟動。|  
|[CAsyncMonikerFile::OnStopBinding](../Topic/CAsyncMonikerFile::OnStopBinding.md)|呼叫時，非同步傳輸已停止。|  
  
## 備註  
 從 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)衍生，從 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)又衍生自類別， `CAsyncMonikerFile` 使用 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) 介面從 URL 存取所有資料流以非同步方式，包括載入檔案非同步。  檔案可以是 ActiveX 控制項 datapath 屬性。  
  
 非同步標記主要在網際網路上啟用應用程式和 ActiveX 控制項提供一種敏感性使用者介面在檔案傳輸期間。  這個燈光類系統的主要範例是使用 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) 之 ActiveX 控制項提供非同步屬性。  `CDataPathProperty` 物件會重複地取得回呼在冗長的屬性交換處理序的最新資料的可用性。  
  
 如需如何使用非同步標記和 ActiveX 控制項的詳細資訊在網際網路應用程式，請參閱下列文件:  
  
-   [網際網路第一個步驟:非同步標記](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [網際網路第一個步驟:ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 `CAsyncMonikerFile`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [CMonikerFile Class](../../mfc/reference/cmonikerfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMonikerFile Class](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)   
 [Asynchronous Versus Synchronous Monikers](http://msdn.microsoft.com/library/windows/desktop/ms687193)