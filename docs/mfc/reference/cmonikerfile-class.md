---
title: "CMonikerFile Class | Microsoft Docs"
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
  - "CMonikerFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonikerFile class"
  - "IMoniker interface"
  - "IMoniker interface, 繫結"
  - "monikers, MFC"
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMonikerFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)\([IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)\) 命名的資料流。  
  
## 語法  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMonikerFile::CMonikerFile](../Topic/CMonikerFile::CMonikerFile.md)|建構 `CMonikerFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMonikerFile::Close](../Topic/CMonikerFile::Close.md)|中斷連接並釋放資料流並釋放 Moniker。|  
|[CMonikerFile::Detach](../Topic/CMonikerFile::Detach.md)|中斷與這個物件的 `CMonikerFile``IMoniker` 。|  
|[CMonikerFile::GetMoniker](../Topic/CMonikerFile::GetMoniker.md)|傳回目前 Moniker。|  
|[CMonikerFile::Open](../Topic/CMonikerFile::Open.md)|開啟指定的檔案取得資料流。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMonikerFile::CreateBindContext](../Topic/CMonikerFile::CreateBindContext.md)|取得繫結內容或建立預設使用的繫結內容。|  
  
## 備註  
 Moniker 包含資訊很像路徑名稱加入至檔案。  如果您已經有指標 Moniker 物件的 `IMoniker` 介面，則可以取得識別檔案的存取權限沒有實際檔案所在的任何其他特定資訊。  
  
 從 `COleStreamFile`衍生， `CMonikerFile` 接受它可以製作為 Moniker 和繫結至資料流 Moniker 是一個名稱的 Moniker 或字串表示。  您可以寫入該資料流、讀取和寫入。  `CMonikerFile` 虛擬的目的是要提供給 `IMoniker`s 的簡單存取名為的 `IStream`\)，讓您不必繫結至資料流，具有 `CFile` 功能，為資料流。  
  
 除了資料流以外，`CMonikerFile` 無法用來繫結至任何項目。  如果您想要繫結至儲存區或物件，您必須直接使用 `IMoniker` 介面。  
  
 如需資料流和標記的詳細資訊，請參閱《 *MFC* 參考和 [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) 的 [COleStreamFile](../../mfc/reference/colestreamfile-class.md) 和 [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) 在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [COleStreamFile Class](../../mfc/reference/colestreamfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile Class](../../mfc/reference/casyncmonikerfile-class.md)