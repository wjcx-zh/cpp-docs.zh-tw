---
title: IDBCreateCommandImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6d8a07ded3da02c21c4ee8c528474efc6e52b6c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021560"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl 類別

提供實作[IDBCreateCommand](/previous-versions/windows/desktop/ms711625\(v=vs.85\))介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>參數  

*T*<br/>
工作階段物件衍生自`IDBCreateCommandImpl`。  
  
*CommandClass*<br/>
您的命令類別。  

## <a name="requirements"></a>需求  

**Header:** atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[CreateCommand](#createcommand)|建立新的命令。|  
  
## <a name="remarks"></a>備註  

若要取得新的命令的工作階段物件上選擇性的介面。  

## <a name="createcommand"></a> Idbcreatecommandimpl:: Createcommand

建立新的命令，並傳回要求的介面。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>參數  

請參閱[idbcreatecommand:: Createcommand](/previous-versions/windows/desktop/ms709772\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
某些參數會對應至*OLE DB 程式設計人員參考*參數中所述的不同名稱的`IDBCreateCommand::CreateCommand`:  
  
|OLE DB 範本參數|*OLE DB 程式設計人員參考*參數|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)