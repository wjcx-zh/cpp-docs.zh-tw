---
title: 範圍 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.range
dev_langs:
- C++
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4bf4f02043f3cb11a47357ff91898da23ed03c22
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014204"
---
# <a name="range-c"></a>range (C++)
指定引數或在執行階段設定其值的欄位的允許值的範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ range(  
   low,   
   high  
) ]  
```  
  
### <a name="parameters"></a>參數  
 *low*  
 下限範圍值。  
  
 *high*  
 高範圍的值。  
  
## <a name="remarks"></a>備註  
 **範圍**c + + 屬性具有相同的功能[範圍](http://msdn.microsoft.com/library/windows/desktop/aa367151)MIDL 屬性。  
  
## <a name="example"></a>範例  
  
```cpp  
// cpp_attr_ref_range.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);  
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|介面方法，介面參數|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [方法屬性](../windows/method-attributes.md)   
 [參數屬性](../windows/parameter-attributes.md)   
 [資料成員屬性](../windows/data-member-attributes.md)   