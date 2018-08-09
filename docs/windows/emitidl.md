---
title: emitidl |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.emitidl
dev_langs:
- C++
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c52b905420dcb576705d63be7d7bdce27c5eea6
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015239"
---
# <a name="emitidl"></a>emitidl
指定是否正在處理所有後續的 IDL 屬性，並放在所產生的.idl 檔案中。  
  
## <a name="syntax"></a>語法  
  
```cpp
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>參數  
*state*  
其中一個可能的值： `true`， `false`， `forced`， `restricted`， `push`，或`pop`。  
  
-   如果`true`，在原始程式碼檔案中遇到的任何 IDL 類別目錄屬性會放在所產生的.idl 檔案。 這是預設設定，如**emitidl**。  
  
-   如果`false`，在原始程式碼檔案中遇到的任何 IDL 類別屬性未放置在所產生的.idl 檔案。  
  
-   如果`restricted`，允許在不含檔案中的 IDL 屬性[模組](../windows/module-cpp.md)屬性。 編譯器不會產生的.idl 檔案。  
  
-   如果`forced`，會覆寫的後續`restricted`屬性，需要有檔案`module`屬性如果 IDL 屬性檔案中。  
  
-   `push` 可讓您儲存目前**emitidl**設定為內部**emitidl**堆疊，並`pop`可讓您設定**emitidl**到頂端的 內部的任何值是**emitidl**堆疊。  
  
`defaultimports=`*布林值*\(選擇性)  
-   如果*布林*是 **，則為 true**，docobj.idl 匯入所產生的.idl 檔案。 此外，如果.idl 檔同名的.h 檔案`#include`到您的來源與.h 檔案中，相同的目錄中找到程式碼，則產生的.idl 檔案將包含該.idl 檔案匯入陳述式。  
  
-   如果*布林*是**false**，docobj.idl 不會匯入所產生的.idl 檔案。 您必須明確地匯入.idl 檔案[匯入](../windows/import.md)。  
  
## <a name="remarks"></a>備註  
在後**emitidl**原始程式碼檔案中發生 c + + 屬性、 類別目錄的 IDL 屬性會放在所產生的.idl 檔案。 如果沒有任何**emitidl**原始程式碼檔案中的 IDL 屬性的屬性，會輸出到產生的.idl 檔案。  
  
很可能有多個**emitidl**原始程式碼檔案中的屬性。 如果`[emitidl(false)];`沒有後續的檔案中遇到`[emitidl(true)];`，則沒有屬性，都會處理到所產生的.idl 檔案。  
  
編譯器遇到新的檔案，每次**emitidl**隱含地設定為 **，則為 true**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
[編譯器屬性](../windows/compiler-attributes.md)   
[獨立屬性](../windows/stand-alone-attributes.md)   
[屬性範例](http://msdn.microsoft.com/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)