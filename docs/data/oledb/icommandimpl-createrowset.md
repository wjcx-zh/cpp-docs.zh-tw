---
title: "Icommandimpl:: Createrowset |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
dev_langs: C++
helpviewer_keywords: CreateRowset method
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 510f222972b8d9306f7b248799679f0dd499288a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="icommandimplcreaterowset"></a>ICommandImpl::CreateRowset
由呼叫[Execute](../../data/oledb/icommandimpl-execute.md)建立單一資料列集。  
  
## <a name="syntax"></a>語法  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### <a name="parameters"></a>參數  
 `RowsetClass`  
 代表使用者的資料列集類別的樣板類別成員。 通常是由精靈產生。  
  
 `pUnkOuter`  
 [in]若要控制的指標**IUnknown**介面的資料列集建立為彙總的一部分，否則便是 null。  
  
 `riid`  
 [in]對應至`riid`中`ICommand::Execute`。  
  
 `pParams`  
 [輸入/輸出]對應至`pParams`中`ICommand::Execute`。  
  
 `pcRowsAffected`  
 對應至`pcRowsAffected`中`ICommand::Execute`。  
  
 `ppRowset`  
 [輸入/輸出]對應至`ppRowset`中`ICommand::Execute`。  
  
 `pRowsetObj`  
 [out]資料列集物件的指標。 通常不使用此參數，但如果您必須從資料列集執行更多工作，才能將它傳遞給 COM 物件才能使用。 存留期`pRowsetObj`受限於`ppRowset`。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。 請參閱`ICommand::Execute`的一般值的清單。  
  
## <a name="remarks"></a>備註  
 若要建立多個資料列集，或提供您自己的條件建立不同的資料列集，將不同的呼叫`CreateRowset`從**Execute**。  
  
 請參閱[icommand:: Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx)中*OLE DB 程式設計人員參考。*  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)