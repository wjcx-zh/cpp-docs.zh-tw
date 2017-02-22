---
title: "COleStreamFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleStreamFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleStreamFile class"
  - "data streams [C++]"
  - "data streams [C++], OLE"
  - "OLE [C++], streams of data"
  - "OLE structured storage [C++]"
  - "streams [C++], OLE"
  - "structured storage in OLE"
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleStreamFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示資料流 \(`IStream`\) 做為 OLE 結構化儲存體的一部分，在複合檔案。  
  
## 語法  
  
```  
class COleStreamFile : public CFile  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleStreamFile::COleStreamFile](../Topic/COleStreamFile::COleStreamFile.md)|建構 `COleStreamFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleStreamFile::Attach](../Topic/COleStreamFile::Attach.md)|關聯資料流的物件。|  
|[COleStreamFile::CreateMemoryStream](../Topic/COleStreamFile::CreateMemoryStream.md)|若要從全域記憶體的資料流並與物件相關聯。|  
|[COleStreamFile::CreateStream](../Topic/COleStreamFile::CreateStream.md)|建立資料流並與物件相關聯。|  
|[COleStreamFile::Detach](../Topic/COleStreamFile::Detach.md)|解除物件的資料流。|  
|[COleStreamFile::GetStream](../Topic/COleStreamFile::GetStream.md)|傳回目前的資料流。|  
|[COleStreamFile::OpenStream](../Topic/COleStreamFile::OpenStream.md)|安全地開啟資料流並與物件相關聯。|  
  
## 備註  
 `IStorage` 物件必須存在，才能開啟資料流或建立之前，除非它是記憶體資料流。  
  
 `COleStreamFile` 物件來操作方式 [C 檔案](../../mfc/reference/cfile-class.md) 物件。  
  
 如需作業的資料流和儲存區的詳細資訊，請參閱本文。 [容器:複合檔案](../../mfc/containers-compound-files.md)。  
  
 如需詳細資訊，請參閱 [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) 和 [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) 在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)