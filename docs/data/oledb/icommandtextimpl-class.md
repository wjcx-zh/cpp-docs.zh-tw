---
title: ICommandTextImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f49326dba4868ad490dc1a7122eed68271bdfa15
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100196"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 類別
提供的實作[ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 命令類別衍生自**ICommandTextImpl**。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|傳回上次呼叫所設定的文字命令[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|設定命令文字，取代現有的命令文字。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|儲存命令文字。|  
  
## <a name="remarks"></a>備註  
 在命令中的強制介面。  
  
## <a name="requirements"></a>需求  
 **標頭：** altdb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)