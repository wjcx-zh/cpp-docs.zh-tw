---
title: "Cdberrorinfo:: Getcustomerrorobject |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
dev_langs: C++
helpviewer_keywords: GetCustomErrorObject method
ms.assetid: 295c053c-b76c-47a5-adfb-333e65d2df0d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9367c048ec78990f0544c745256a27916b46f919
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdberrorinfogetcustomerrorobject"></a>CDBErrorInfo::GetCustomErrorObject
呼叫[IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx)來傳回自訂錯誤物件介面的指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT GetCustomErrorObject(   
   ULONG ulRecordNum,   
   REFIID riid,   
   IUnknown** ppObject    
) const throw( );  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)