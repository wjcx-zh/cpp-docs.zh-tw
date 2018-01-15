---
title: "emitidl |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.emitidl
dev_langs: C++
helpviewer_keywords: emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55fc74eef3d2ead7312f7dca46f20c3a1ed7ba91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="emitidl"></a>emitidl
指定是否會處理所有後續的 IDL 屬性，並放入產生的.idl 檔案。  
  
## <a name="syntax"></a>語法  
  
```
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>參數  
*state*  
其中一個可能的值： **true**， **false**，**強制**，**限制**，**發送**，或**pop**。  
  
-   如果**true**，原始程式碼檔案中遇到的任何 IDL 類別目錄屬性會放在產生的.idl 檔案。 這是預設設定**emitidl**。  
  
-   如果**false**，原始程式碼檔案中遇到的任何 IDL 類別屬性未放置在產生的.idl 檔案。  
  
-   如果**限制**，可讓不含的檔案中的 IDL 屬性[模組](../windows/module-cpp.md)屬性。 編譯器不會產生.idl 檔案。  
  
-   如果**強制**，會覆寫後續**限制**屬性，需要有檔案**模組**屬性如果 IDL 屬性檔案中。  
  
-   **推入**可讓您儲存目前**emitidl**內部設定**emitidl**堆疊，以及**pop**可讓您設定**emitidl**到任何值是在內部的頂端**emitidl**堆疊。  
  
`defaultimports=`*布林*\(選擇性)  
-   如果*布林*是**true**，docobj.idl 匯入產生的.idl 檔案。 此外，如果.idl 檔同名的.h 檔案您`#include`到您的來源與.h 檔案中，相同的目錄中找到程式碼，則產生的.idl 檔案包含該.idl 檔案匯入陳述式。  
  
-   如果*布林*是**false**，docobj.idl 不會匯入產生的.idl 檔案。 您必須明確匯入具有.idl 檔案[匯入](../windows/import.md)。  
  
## <a name="remarks"></a>備註  
之後**emitidl**原始程式碼檔案中遇到 c + + 屬性、 類別目錄的 IDL 屬性會放在產生的.idl 檔案。 如果沒有任何**emitidl**原始程式碼檔案中的 IDL 屬性的屬性，會輸出到產生的.idl 檔案。  
  
它是可能有多個**emitidl**原始程式碼檔案中的屬性。 如果`[emitidl(false)];`在沒有後續的檔案時發現`[emitidl(true)];`，則屬性不會處理到產生的.idl 檔案。  
  
編譯器遇到新的檔案，每次**emitidl**會隱含地設**true**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|任何位置|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
[編譯器屬性](../windows/compiler-attributes.md)   
[獨立屬性](../windows/stand-alone-attributes.md)   
[屬性範例](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)