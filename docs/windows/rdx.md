---
title: rdx |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.rdx
dev_langs:
- C++
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7647ca56e3159564826efa9caf438456b9ae3568
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878953"
---
# <a name="rdx"></a>rdx
建立登錄機碼或修改現有的登錄機碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### <a name="parameters"></a>參數  
 `key`  
 若要建立或開啟索引鍵的名稱。  
  
 `valuename` (選擇性)  
 指定要設定的值欄位。 如果在索引鍵已經存在具有此名稱的值欄位，會將它加入。  
  
 *regtype*  
 要加入的登錄機碼的類型。 可以是下列其中之一：**文字**， **dword**，**二進位**，或`CString`。  
  
## <a name="remarks"></a>備註  
 **Rdx** c + + 屬性建立或修改現有的登錄機碼的 COM 元件。 屬性會新增 BEGIN_RDX_MAP 巨集來實作目標成員的物件。 `RegistryDataExchange`插入 BEGIN_RDX_MAP 巨集，因為函式可以用來登錄和資料成員之間傳送資料  
  
 這個屬性可以用於搭配[coclass](../windows/coclass.md)， [progid](../windows/progid.md)，或[vi_progid](../windows/vi-progid.md)屬性或表示下列其中一種其他屬性。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**或`struct`成員|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="example"></a>範例  
 下列程式碼新增至描述 CMyClass COM 元件的系統呼叫 MyValue 登錄機碼。  
  
```  
// cpp_attr_ref_rdx.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
  
[module (name="MyLib")];  
  
class CMyClass {  
public:  
   CMyClass() {  
      strcpy_s(m_sz, "SomeValue");  
   }  
  
   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]   
   char m_sz[256];  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [COM 屬性](../windows/com-attributes.md)   
 [registration_script](../windows/registration-script.md)   
