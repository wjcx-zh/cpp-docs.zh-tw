---
title: progid |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2b2d2168b568c74c5404cc83bab1e5f77570773
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880429"
---
# <a name="progid"></a>progid
指定 COM 物件的 ProgID。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>參數  
 *name*  
 代表物件的 ProgID。  
  
 Progid 呈現人類看得懂的版本，用來識別 COM/ActiveX 物件的類別識別項 (CLSID)。  
  
## <a name="remarks"></a>備註  
 **Progid** c + + 屬性可讓您指定 COM 物件的 ProgID。 ProgID 已表單*name1.name2.version*。 如果您未指定*版本*ProgID 的預設版本為 1。 如果您未指定*name1.name2*的預設名稱是*classname.classname*。 如果您未指定**progid** ，而且您指定**vi_progid**， *name1.name2*摘錄自**vi_progid**和 (下一個循序附加數字） 版本。  
  
 如果使用屬性區塊**progid**也不使用`uuid`，編譯器會檢查登錄，以查看是否`uuid`存在指定**progid**。 如果**progid**未指定，版本 （和 coclass 的名稱，如果建立在 coclass） 會用來產生**progid**。  
  
 **progid**意味著**coclass**屬性，也就是如果您指定**progid**，這是與指定的相同動作**coclass**和**progid**屬性。  
  
 **Progid**屬性會造成自動註冊指定的名稱下的類別。 將不會顯示產生的.idl 檔案**progid**值。  
  
 使用 ATL 專案中使用這個屬性時，屬性的行為變更。 除了上述的行為，使用這個屬性指定的資訊用於**GetProgID**函式，由插入**coclass**屬性。 如需詳細資訊，請參閱[coclass](../windows/coclass.md)屬性。  
  
## <a name="example"></a>範例  
 請參閱範例的[coclass](../windows/coclass.md)的範例使用**progid**。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [ProgID 的索引鍵](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
