---
title: coclass |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.coclass
dev_langs:
- C++
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2043ca568f36d7fc0eaaffbf940cabb423de5620
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647836"
---
# <a name="coclass"></a>coclass
建立 COM 物件，可實作 COM 介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
[coclass]  
```  
  
## <a name="remarks"></a>備註  
 **Coclass** c + + 屬性會置於所產生的.idl 檔案中的 coclass 建構。  
  
 在定義的 coclass 時，您也可以指定[uuid](../windows/uuid-cpp-attributes.md)，[版本](../windows/version-cpp.md)，[執行緒](../windows/threading-cpp.md)， [vi_progid](../windows/vi-progid.md)，和[progid](../windows/progid.md)屬性。 如果未指定其中任何一個，它將會產生。  
  
 如果兩個標頭檔包含具有類別**coclass**屬性，而不指定 GUID，編譯器會使用相同的 GUID，這兩個類別，並會導致 MIDL 錯誤。  因此，您應該使用`uuid`屬性使用時**coclass**。  
  
 **ATL 專案**  
  
 當這個屬性在 ATL 專案中，前面的類別或結構的定義時它：  
  
-   插入程式碼或資料，以支援自動註冊的物件。  
  
-   插入程式碼或資料，以支援 COM class factory 物件。  
  
-   插入程式碼或資料，以實作`IUnknown`並讓物件可建立 COM 物件。  
  
 具體而言，下列的基底類別會加入至目標物件：  
  
-   [CComCoClass 類別](../atl/reference/ccomcoclass-class.md)提供之物件的預設類別處理站和彙總模型。  
  
-   [CComObjectRootEx 類別](../atl/reference/ccomobjectrootex-class.md)具有根據指定的執行緒模型類別樣板[執行緒](../windows/threading-cpp.md)屬性。 如果`threading`屬性未指定，預設的執行緒模型為 apartment。  
  
-   [IProvideClassInfo2Impl](../atl/reference/iprovideclassinfo2impl-class.md)如果加入[noncreatable](../windows/noncreatable.md)屬性未指定目標物件。  
  
 最後，任何未定義使用內嵌的 IDL 的雙重介面會取代具有對應[IDispatchImpl](../atl/reference/idispatchimpl-class.md)類別。 如果在內嵌 IDL 中定義的雙重介面，則不會修改基底清單中的特定介面。  
  
 **Coclass**屬性也可讓下列函式提供透過插入程式碼，或是這種案例`GetObjectCLSID`，做為基底類別中的靜態方法`CComCoClass`:  
  
-   `UpdateRegistry` 註冊目標類別的 class 的 factory。  
  
-   `GetObjectCLSID`相關的註冊，也可用來取得目標類別的 CLSID。  
  
-   `GetObjectFriendlyName` 根據預設會傳回的格式字串"\<*目標類別名稱*> `Object`"。 如果此函式已存在於，它不會加入。 新增此函式至目標類別，以傳回較容易使用的名稱，比自動產生。  
  
-   `GetProgID`相關的註冊，會傳回與指定的字串[progid](../windows/progid.md)屬性。  
  
-   `GetVersionIndependentProgID` 具有相同的功能`GetProgID`，但它會傳回與指定的字串[vi_progid](../windows/vi-progid.md)。  
  
 下列變更，與相關的 COM 對應，會對目標類別：  
  
-   COM 對應的目標類別衍生自的所有介面的項目與所指定的所有項目加入[COM 介面進入點](../mfc/com-interface-entry-points.md)屬性，或所需的那些[彙總](../windows/aggregates.md)屬性。  
  
-   [OBJECT_ENTRY_AUTO](../atl/reference/object-map-macros.md#object_entry_auto)巨集插入到 COM 對應。
  
 產生類別的.idl 檔案中 coclass 的名稱必須與類別相同的名稱。  如範例中，並參考下列範例中，若要存取在 coclass 的類別識別碼`CMyClass`，在用戶端透過 MIDL 產生的標頭檔，使用`CLSID_CMyClass`。  
  
## <a name="example"></a>範例  
 下列程式碼示範如何使用**coclass**屬性：  
  
```cpp  
// cpp_attr_ref_coclass1.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="MyLib")];  
  
[ object, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface I {  
   HRESULT func();  
};  
  
[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),   
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]  
class CMyClass : public I {};  
```  
  
 下列範例示範如何覆寫函式所插入的程式碼中所顯示的預設實作**coclass**屬性。 如需檢視插入程式碼的詳細資訊，請參閱 [/Fx](../build/reference/fx-merge-injected-code.md) 。 任何基底類別或您使用類別的介面會出現在 插入程式碼。 此外，如果類別包含預設會在插入程式碼並明確指定該類別作為基底您 coclass，屬性提供者會使用您的程式碼中指定的格式。  
  
```cpp  
// cpp_attr_ref_coclass2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
[module(name="MyLib")];  
  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface bb {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class CMyClass : public bb {  
public:  
   // by adding the definition of UpdateRegistry to your code,   
   // the function will not be included in the injected code  
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {  
      // you can add to the default implementation  
      CRegistryVirtualMachine rvm;  
      HRESULT hr;  
      if (FAILED(hr = rvm.AddStandardReplacements()))  
         return hr;  
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());  
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),  
         GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);  
   }  
};  
```  
  
## <a name="requirements"></a>需求  
  
### <a name="attribute-context"></a>屬性內容  
  
|||  
|-|-|  
|**適用於**|**類別**，**結構**|  
|**可重複**|否|  
|**必要屬性**|無|  
|**無效屬性**|無|  
  
 如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另請參閱  
 [IDL 屬性](../windows/idl-attributes.md)   
 [COM 屬性](../windows/com-attributes.md)   
 [類別屬性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [appobject](../windows/appobject.md)