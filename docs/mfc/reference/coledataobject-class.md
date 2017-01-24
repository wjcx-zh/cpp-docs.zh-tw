---
title: "COleDataObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDataObject"
  - "COleDataObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "剪貼簿 [C++], MFC 支援"
  - "剪貼簿 [C++], OLE 支援"
  - "COleDataObject class"
  - "data transfer [C++]"
  - "data transfer [C++], OLE"
  - "drag and drop [C++], MFC 支援"
  - "IDataObject interface, MFC encapsulation"
  - "OLE [C++], uniform data transfer"
  - "OLE Clipboard [C++], 支援"
  - "OLE data transfer [C++]"
  - "uniform data transfer"
  - "uniform data transfer, OLE"
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDataObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用在資料傳輸用於擷取資料的各種格式從剪貼簿，透過拖放作業，或從內嵌 OLE 項目。  
  
## 語法  
  
```  
class COleDataObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDataObject::COleDataObject](../Topic/COleDataObject::COleDataObject.md)|建構 `COleDataObject` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDataObject::Attach](../Topic/COleDataObject::Attach.md)|附加至 `COleDataObject`的指定 OLE 資料物件。|  
|[COleDataObject::AttachClipboard](../Topic/COleDataObject::AttachClipboard.md)|附加在剪貼簿上的資料物件。|  
|[COleDataObject::BeginEnumFormats](../Topic/COleDataObject::BeginEnumFormats.md)|提供一或多個後續的 `GetNextFormat` 呼叫。|  
|[COleDataObject::Detach](../Topic/COleDataObject::Detach.md)|中斷連結 `IDataObject` 相關聯的物件。|  
|[COleDataObject::GetData](../Topic/COleDataObject::GetData.md)|複製附加的 OLE 資料物件的資料是以指定的格式。|  
|[COleDataObject::GetFileData](../Topic/COleDataObject::GetFileData.md)|複製附加的 OLE 資料物件的資料轉換成指定格式的一 `CFile` 指標。|  
|[COleDataObject::GetGlobalData](../Topic/COleDataObject::GetGlobalData.md)|複製附加的 OLE 資料物件的資料轉換成指定格式的 `HGLOBAL` 。|  
|[COleDataObject::GetNextFormat](../Topic/COleDataObject::GetNextFormat.md)|傳回下一個可用的資料格式。|  
|[COleDataObject::IsDataAvailable](../Topic/COleDataObject::IsDataAvailable.md)|若要檢查資料是否可從指定的格式。|  
|[COleDataObject::Release](../Topic/COleDataObject::Release.md)|中斷連接並釋放相關聯的 `IDataObject` 物件。|  
  
## 備註  
 `COleDataObject` 不具有基底類別。  
  
 這類資料傳送包含一個來源和目的端。  資料來源實作， [COleDataSource](../../mfc/reference/coledatasource-class.md) 類別的物件。  每當接收端應用程式具有置放的資料或要求執行從剪貼簿貼上作業，必須建立 `COleDataObject` 類別的物件。  
  
 這個類別可讓您判斷資料是否存在於指定的格式。  您也可以列舉可用的資料格式或檢查特定格式是否可以再擷取在慣用格式的資料。  擷取物件可以完成使用幾種不同方式，包括使用 [C 檔案](../../mfc/reference/cfile-class.md)、 `HGLOBAL`或 **STGMEDIUM** 結構。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) 結構。  
  
 如需使用資料物件的詳細資訊會儲存在您的應用程式，請參閱本文 [資料物件和資料來源 \(Object Linking\)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
## 繼承階層架構  
 `COleDataObject`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDataSource Class](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)   
 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)   
 [CView::OnDrop](../Topic/CView::OnDrop.md)