---
title: no_injected_text |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc0dcba6597b6b8a3b37c240bf1c4a58f30b6b23
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020339"
---
# <a name="noinjectedtext"></a>no_injected_text
防止編譯器將程式碼，因為屬性使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ no_injected_text(  
   boolean  
) ];  
```  
  
### <a name="parameters"></a>參數  
 *布林*（選擇性）  
 **真**如果您想不要插入此項目，任何程式碼**false**讓插入的程式碼。 **true**是預設值。  
  
## <a name="remarks"></a>備註  
 最常見的用法**no_injected_text** c + + 屬性是由[/Fx](../build/reference/fx-merge-injected-code.md)編譯器選項，插入**no_injected_text**到.mrg 檔的屬性。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器屬性](../windows/compiler-attributes.md)   