---
title: "執行緒 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.threading
dev_langs: C++
helpviewer_keywords: threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e44fec96391fff6700ecf4a453d7455bd75e9df7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="threading-c"></a>threading (C++)
指定 COM 物件的執行緒模型。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 ***模型***（選擇性）  
 下列的執行緒模型其中一項：  
  
-   **apartment** （apartment 執行緒）  
  
-   **中性**（沒有使用者介面的.NET Framework 元件）  
  
-   **單一**（簡單執行緒）  
  
-   **免費**（免費執行緒）  
  
-   **同時**（apartment 和無限制執行緒）  
  
 預設值是**apartment**。  
  
## <a name="remarks"></a>備註  
 **執行緒**c + + 屬性不會出現在產生的.idl 檔案中，但將會使用您的 COM 物件的實作。  
  
 在 ATL 專案中，如果[coclass](../windows/coclass.md)屬性也會出現，所指定的執行緒模型*模型*傳遞為範本參數[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)類別插入**coclass**屬性。  
  
 **執行緒**屬性也會保護存取[event_source](../windows/event-source.md)。  
  
## <a name="example"></a>範例  
 請參閱[授權](../windows/licensed.md)範例使用範例**執行緒**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|**coclass**|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [COM 屬性](../windows/com-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [多執行緒支援對舊版程式碼 （Visual c + +）](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [中性 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
