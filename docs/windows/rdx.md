---
title: rdx |Microsoft Docs
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
ms.openlocfilehash: 32dd702dd7d429c4437875a6aead86ae687dfb2b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011045"
---
# <a name="rdx"></a>rdx
建立登錄機碼或修改現有的登錄機碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
### <a name="parameters"></a>參數  
 *key*  
 若要建立或開啟金鑰的名稱。  
  
 *valuename* （選擇性）  
 指定要設定的 [值] 欄位。 如果在索引鍵已經存在具有此名稱的值欄位，會將它加入。  
  
 *regtype*  
 要加入的登錄機碼的類型。 可以是下列其中之一： `text`， `dword`， `binary`，或`CString`。  
  
## <a name="remarks"></a>備註  
 **Rdx** c + + 屬性建立或修改現有的登錄機碼的 COM 元件。 屬性會將 BEGIN_RDX_MAP 巨集將實作的目標成員的物件。 `RegistryDataExchange`插入 BEGIN_RDX_MAP 巨集，因為函式可以用來登錄和資料成員之間傳輸資料  
  
 這個屬性可以用於搭配[coclass](../windows/coclass.md)， [progid](../windows/progid.md)，或[vi_progid](../windows/vi-progid.md)屬性或其他屬性，表示其中一種。  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**或是**struct**成員|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會加入稱為 MyValue 系統描述 CMyClass COM 元件的登錄機碼。  
  
```cpp  
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