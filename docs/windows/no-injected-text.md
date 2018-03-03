---
title: "no_injected_text |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c74d3134b5381be4ec330742726b26fea6155da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="noinjectedtext"></a>no_injected_text
防止編譯器插入程式碼，因為屬性使用。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ no_injected_text(  
   boolean  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 `boolean` (選擇性)  
 **true**如果您想不要插入的程式，任何程式碼**false**允許無法插入的程式碼。 **true**是預設值。  
  
## <a name="remarks"></a>備註  
 最常見的用法**no_injected_text** c + + 屬性是由[/Fx](../build/reference/fx-merge-injected-code.md)編譯器選項，它會插入**no_injected_text**到.mrg 檔中的屬性。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   
