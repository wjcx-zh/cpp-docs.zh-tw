---
title: 識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.id
dev_langs:
- C++
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b36a45dad71f2144c3e3d0990ab7715d00e8ff21
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605704"
---
# <a name="id"></a>id
指定*dispid* （屬性或方法，在介面或 dispinterface） 的成員函式的參數。  
  
## <a name="syntax"></a>語法  
  
```  
[ id(  
   dispid  
) ]  
```  
  
### <a name="parameters"></a>參數  
 *dispid*  
 介面方法的分派識別碼。  
  
## <a name="remarks"></a>備註  
 **識別碼**c + + 屬性具有相同的功能[識別碼](http://msdn.microsoft.com/library/windows/desktop/aa367040)MIDL 屬性。  
  
## <a name="example"></a>範例  
 範例，請參閱[可繫結](../windows/bindable.md)如需如何使用的範例**識別碼**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|介面方法|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [資料成員屬性](../windows/data-member-attributes.md)   
 [預設值](../windows/defaultvalue.md)   
 [in](../windows/in-cpp.md)   
 [out](../windows/out-cpp.md)   