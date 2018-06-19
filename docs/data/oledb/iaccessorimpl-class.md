---
title: IAccessorImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d62deeb487fded5895bbd47332a0f8a6ad7bbce6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102520"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl 類別
提供的實作[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T, 
          class BindType = ATLBINDINGS,
          class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的資料列集或命令的物件類別。  
  
 `BindType`  
 存放裝置的繫結資訊。 預設值是**ATLBINDINGS**結構 （請參閱為 atldb）。  
  
 `BindingVector`  
 存放裝置的資料行資訊。 預設值是[CAtlMap](../../atl/reference/catlmap-class.md)所在的索引鍵的項目**HACCESSOR**值和值的項目是指標`BindType`結構。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)|建構函式。|  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)|將參考計數加入至現有的存取子。|  
|[CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)|從一組繫結建立存取子。|  
|[GetBindings](../../data/oledb/iaccessorimpl-getbindings.md)|傳回的繫結的存取子中。|  
|[ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)|釋放存取子。|  
  
## <a name="remarks"></a>備註  
 這是必要的資料列集和命令。 OLE DB 需要實作的提供者**HACCESSOR**，即為陣列的標記[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)結構。 **HACCESSOR**所提供的 s`IAccessorImpl`是位址`BindType`結構。 根據預設，`BindType`定義為**ATLBINDINGS**中`IAccessorImpl`的樣板定義。 `BindType` 提供所使用的機制`IAccessorImpl`追蹤中的項目數其**DBBINDING**以及參考計數和存取子旗標的陣列。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)