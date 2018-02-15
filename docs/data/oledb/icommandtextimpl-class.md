---
title: "ICommandTextImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 397f7b26d9f75813897309c99c40d5db94f06c53
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
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
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)