---
title: 彙總 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.aggregatable
dev_langs:
- C++
helpviewer_keywords:
- aggregatable attribute
ms.assetid: 9253a46a-cd76-41f2-b3b6-86f709bb069c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1d80b2fb707145f698e8d9bb883059478c3da10b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="aggregatable"></a>aggregatable
表示此類別支援彙總。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ aggregatable(   
   value  
) ]  
```  
  
#### <a name="parameters"></a>參數  
 *值*（選擇性）  
 表示 COM 物件可以彙總的參數：  
  
-   **永遠不會**無法彙總的 COM 物件。  
  
-   **允許**可以直接建立 COM 物件，或可以彙總。 這是預設值。  
  
-   **一律**COM 物件無法直接建立，且只會彙總。 當您呼叫`CoCreateInstance`此物件，您必須指定彙總物件的**IUnknown**介面 (控制**IUnknown**)。  
  
## <a name="remarks"></a>備註  
 **彙總**c + + 屬性具有相同的功能[彙總](http://msdn.microsoft.com/library/windows/desktop/aa366721)MIDL 屬性。 這表示編譯器將會通過**彙總**透過屬性設定為產生的.idl 檔案。  
  
 此屬性需要 [coclass](../windows/coclass.md)、 [progid](../windows/progid.md)或 [vi_progid](../windows/vi-progid.md) 屬性 (或表示上述其中一項的另一個屬性) 也套用至相同的項目。 如果使用任何單一屬性，則會自動套用其他兩項。 例如，如果套用 **progid** ，則也會套用 **vi_progid** 和 **coclass** 。  
  
 **ATL 專案**  
  
 如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 除了上述的行為，此屬性也會加入下列巨集的其中一個目標類別：  
  
|參數值|插入的巨集|  
|---------------------|--------------------|  
|**永遠不會**|[DECLARE_NOT_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_not_aggregatable)|  
|**允許**|[DECLARE_POLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_poly_aggregatable)|  
|**永遠**|[DECLARE_ONLY_AGGREGATABLE](../atl/reference/aggregation-and-class-factory-macros.md#declare_only_aggregatable)|  
  
## <a name="example"></a>範例  
  
```  
// cpp_attr_ref_aggregatable.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="MyModule")];  
  
[ coclass, aggregatable(allowed),  
  uuid("1a8369cc-1c91-42c4-befa-5a5d8c9d2529")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**class**、 `struct`|  
|**可重複**|否|  
|**必要屬性**|下列一或多個項目： **coclass**、 **progid**或 **vi_progid**。|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [彙總](http://msdn.microsoft.com/library/windows/desktop/ms686558)   
