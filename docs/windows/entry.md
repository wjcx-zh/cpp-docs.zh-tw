---
title: 項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db90390be5313ddbea1103105f47b55fe9e23d62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="entry"></a>entry
識別 DLL 中的進入點在模組中指定的匯出函式或常數。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `id`  
 進入點的識別碼。  
  
## <a name="remarks"></a>備註  
 **項目**c + + 屬性具有相同的功能[項目](http://msdn.microsoft.com/library/windows/desktop/aa366815)MIDL 屬性。  
  
## <a name="example"></a>範例  
 請參閱範例的[idl_module](../windows/idl-module.md)使用的範例如**項目**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|`idl_module` 屬性|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
