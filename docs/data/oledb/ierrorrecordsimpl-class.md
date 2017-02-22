---
title: "IErrorRecordsImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IErrorRecordsImpl"
  - "ATL.IErrorRecordsImpl"
  - "IErrorRecordsImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IErrorRecordsImpl 類別"
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IErrorRecordsImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 介面，加入資料錄並擷取資料錄從資料成員 \([m\_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)\) 型別 **CAtlArray\<**`RecordClass`**\>**。  
  
## 語法  
  
```  
template <  
   class T,   
   class RecordClass = ATLERRORINFO  
>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### 參數  
 `T`  
 衍生自 `IErrorRecordsImpl`的類別。  
  
 `RecordClass`  
 代表 OLE DB 錯誤物件的類別。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|從錯誤記錄取得錯誤描述字串。|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|從錯誤記錄有錯誤 GUID。|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|從錯誤記錄取得說明主題代碼。|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|從錯誤記錄取得說明檔的完整路徑名稱。|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|從錯誤記錄取得錯誤原始程式碼。|  
  
### 介面方法  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|將資料錄加入至 OLE DB 錯誤物件。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|傳回有關錯誤的基本資訊，例如傳回碼和提供者特定的錯誤代碼。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|將指標傳回至自訂錯誤物件的介面。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|傳回指定之資料錄的 [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 介面指標。|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|傳回錯誤的參數。|  
|[GetRecordCount](../Topic/CDaoRecordset::GetRecordCount.md)|傳回的資料錄數目 OLE DB 資料錄的物件。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|陣列錯誤記錄。|  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)