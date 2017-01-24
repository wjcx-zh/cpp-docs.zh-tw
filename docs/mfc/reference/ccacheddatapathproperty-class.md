---
title: "CCachedDataPathProperty Class | Microsoft Docs"
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
  - "CCachedDataPathProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 非同步"
  - "asynchronous controls [C++]"
  - "CCachedDataPathProperty class"
  - "memory files [C++]"
  - "OLE 控制項 [C++], 非同步"
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCachedDataPathProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在記憶體檔案實作 OLE 控制項屬性已經傳輸非同步和快取。  
  
## 語法  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](../Topic/CCachedDataPathProperty::CCachedDataPathProperty.md)|建構 `CCachedDataPathProperty` 物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CCachedDataPathProperty::m\_Cache](../Topic/CCachedDataPathProperty::m_Cache.md)|`CMemFile` 物件的快取資料的秒數。|  
  
## 備註  
 記憶體檔案在 RAM 儲存 \(而非從磁碟並提供快速的暫存傳輸會很有用。  
  
 使用 **CAysncMonikerFile** 和 `CDataPathProperty`以外， `CCachedDataPathProperty` 提供功能給 OLE 控制項的非同步標記的使用。  `CCachedDataPathProperty` 物件，您可以從 URL 將資料非同步或檔案來源和儲存在記憶體中傳遞檔案 `m_Cache` 公用變數。  所有資料儲存在記憶體中，所以檔案，不需要覆寫 [OnDataAvailable](../Topic/CAsyncMonikerFile::OnDataAvailable.md) ，除非您要注意告知和回應。  例如，在中，如果您將大型 .GIF 檔案並想要告知您的控制項詳細資料抵達，並且應該重新繪製其本身，覆寫認可告知的 `OnDataAvailable` 。  
  
 類別 `CCachedDataPathProperty``CDataPathProperty`從衍生。  
  
 如需如何使用非同步標記和 ActiveX 控制項的詳細資訊在網際網路應用程式，請參閱下列主題:  
  
-   [網際網路第一個步驟:ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)  
  
-   [網際網路第一個步驟:非同步標記](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## 需求  
 **Header:** afxctl.h  
  
## 請參閱  
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty Class](../../mfc/reference/cdatapathproperty-class.md)