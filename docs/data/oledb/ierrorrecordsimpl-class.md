---
title: "IErrorRecordsImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e69db8c89a60b7dee543bbdf87997514ba5f0cd7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 類別
實作 OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx)介面，加入記錄和資料成員從擷取記錄 ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) 型別的**CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別衍生自`IErrorRecordsImpl`。  
  
 `RecordClass`  
 表示 OLE DB 錯誤物件的類別。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|從錯誤記錄中取得錯誤描述字串。|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|從錯誤記錄中取得錯誤的 GUID。|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|從錯誤記錄中取得的說明內容識別碼。|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|從錯誤記錄中取得說明檔的完整路徑名稱。|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|取得錯誤來源的程式碼從錯誤記錄。|  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|將記錄加入至 OLE DB 錯誤物件。|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|傳回錯誤，例如傳回碼和提供者特定錯誤號碼的相關基本資訊。|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|傳回自訂錯誤物件介面的指標。|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|傳回[IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx)介面指標上指定的記錄。|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|傳回的錯誤參數。|  
|[GetRecordCount](../../mfc/reference/cdaorecordset-class.md#getrecordcount)|OLE DB 記錄物件中傳回記錄的數目。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|錯誤記錄的陣列。|  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)