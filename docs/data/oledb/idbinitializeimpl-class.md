---
title: "IDBInitializeImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
dev_langs: C++
helpviewer_keywords: IDBInitializeImpl class
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a7a51023f167eee5fbd4082486409f4e11a15547
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl 類別
提供的實作[IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx)介面。  
  
## <a name="syntax"></a>語法  
  
```  
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IDBInitializeImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)|建構函式。|  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[初始化](../../data/oledb/idbinitializeimpl-initialize.md)|啟動提供者。|  
|[解除初始化](../../data/oledb/idbinitializeimpl-uninitialize.md)|停止提供者。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_dwStatus](../../data/oledb/idbinitializeimpl-m-dwstatus.md)|資料來源的旗標。|  
|[m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)|實作 DB 屬性資訊的指標。|  
  
## <a name="remarks"></a>備註  
 在資料來源物件與在列舉值的選擇性介面上的強制介面。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)