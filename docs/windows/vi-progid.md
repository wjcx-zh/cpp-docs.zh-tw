---
title: "vi_progid |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.vi_progid
dev_langs: C++
helpviewer_keywords: vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7581a4a10d9f101526aeb1a17ba7e26c4646b39
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="viprogid"></a>vi_progid
指定版本無關的 ProgID 的表單。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
 代表物件的版本無關的 ProgID。  
  
 Progid 呈現人類看得懂的版本，用來識別 COM/ActiveX 物件的類別識別項 (CLSID)。  
  
## <a name="remarks"></a>備註  
 **Vi_progid** c + + 屬性可讓您指定 COM 物件與版本無關的 ProgID。 ProgID 已表單*name1.name2.version*。 沒有與版本無關的 ProgID*版本*。 它是能兩者都指定**progid**和**vi_progid**在 coclass 的屬性。 如果您未指定**vi_progid**、 版本無關的 ProgID 是所指定的值[progid](../windows/progid.md)屬性。  
  
 **vi_progid**意味著**coclass**屬性，也就是如果您指定**vi_progid**，這是與指定的相同動作**coclass**和**vi_progid**屬性。  
  
 **Vi_progid**屬性會造成自動註冊指定的名稱下的類別。 產生的.idl 檔案不會顯示 ProgID 的值。  
  
 在 ATL 專案中，如果[coclass](../windows/coclass.md)屬性也會出現，使用指定的 ProgID **GetVersionIndependentProgID**函式 (插入**coclass**屬性）。  
  
## <a name="example"></a>範例  
 請參閱[coclass](../windows/coclass.md)範例使用範例**vi_progid**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [ProgID 的索引鍵](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
