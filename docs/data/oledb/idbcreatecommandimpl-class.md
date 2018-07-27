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
ms.openlocfilehash: 1ffc92cecb3b28423aa2e869171f730c956996cd
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269747"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl 類別
提供實作[IDBCreateCommand](https://msdn.microsoft.com/library/ms711625.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 工作階段物件衍生自`IDBCreateCommandImpl`。  
  
 *CommandClass*  
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
 請參閱[idbcreatecommand:: Createcommand](https://msdn.microsoft.com/library/ms709772.aspx)中*OLE DB 程式設計人員參考*。  
  
 某些參數會對應至*OLE DB 程式設計人員參考*參數中所述的不同名稱的`IDBCreateCommand::CreateCommand`:  
  
|OLE DB 範本參數|*OLE DB 程式設計人員參考*參數|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
