---
title: coclass （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 0a47f4f503541f9dee67dd8c6cf10297de724a19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232790"
---
# <a name="coclass"></a>coclass

建立可執行 COM 介面的 COM 物件。

## <a name="syntax"></a>語法

```cpp
[coclass]
```

## <a name="remarks"></a>備註

**Coclass** c + + 屬性會將 coclass 結構放在產生的 .idl 檔案中。

定義 coclass 時，您也可以指定[uuid](uuid-cpp-attributes.md)、 [version](version-cpp.md)、[執行緒](threading-cpp.md)、 [vi_progid](vi-progid.md)和[progid](progid.md)屬性。 如果沒有指定任何一個，則會產生它。

如果兩個標頭檔包含具有**coclass**屬性的類別，但未指定 GUID，則編譯器會針對這兩個類別使用相同的 guid，這會導致 MIDL 錯誤。  因此， `uuid` 當您使用**coclass**時，應該使用屬性。

**ATL 專案**

當這個屬性在 ATL 專案中的類別或結構定義之前，它會：

- 插入程式碼或資料，以支持對象的自動註冊。

- 插入程式碼或資料，以支持對象的 COM Class Factory。

- 插入要執行的程式碼或資料 `IUnknown` ，並將物件設為可由 COM 建立的物件。

具體而言，下列基類會新增至目標物件：

- [CComCoClass 類別](../../atl/reference/ccomcoclass-class.md)提供物件的預設 Class Factory 和匯總模型。

- [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)具有以[執行緒](threading-cpp.md)屬性所指定的執行緒模型類別為基礎的範本。 如果 `threading` 未指定屬性，預設的執行緒模型為 [公寓]。

- 如果未指定目標物件的[noncreatable](noncreatable.md)屬性，則會加入[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) 。

最後，未使用內嵌 IDL 定義的任何雙重介面都會取代為對應的[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)類別。 如果在內嵌 IDL 中定義雙重介面，則不會修改基底清單中的特定介面。

**Coclass**屬性也會透過插入的程式碼，或在的案例中提供下列函式， `GetObjectCLSID` 做為基類中的靜態方法 `CComCoClass` ：

- `UpdateRegistry`註冊目標類別的 class factory。

- `GetObjectCLSID`與註冊相關的，也可以用來取得目標類別的 CLSID。

- `GetObjectFriendlyName`根據預設，會傳回格式為 "" 的字串 \<*target class name*> `Object` 。 如果此函式已存在，則不會新增。 將此函式新增至目標類別，以傳回比自動產生的易記名稱。

- `GetProgID`與註冊相關的，會傳回使用[progid](progid.md)屬性指定的字串。

- `GetVersionIndependentProgID`具有和相同的功能 `GetProgID` ，但它會傳回使用[vi_progid](vi-progid.md)所指定的字串。

下列與 COM 對應相關的變更會對目標類別進行：

- 針對目標類別衍生自的所有介面，以及[Com 介面進入點](../../mfc/com-interface-entry-points.md)屬性所指定的所有專案，或是[匯總](aggregates.md)屬性所需的所有專案，都會加入 com 對應。

- [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)宏會插入 COM 對應中。

在該類別的 .idl 檔案中產生的 coclass 名稱，會與類別具有相同的名稱。  例如，和參考下列範例，若要 `CMyClass` 透過 MIDL 產生的標頭檔來存取用戶端中 coclass 的類別識別碼，請使用 `CLSID_CMyClass` 。

## <a name="example"></a>範例

下列程式碼顯示如何使用**coclass**屬性：

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

下列範例示範如何覆寫在**coclass**屬性插入的程式碼中出現的函式的預設執行。 如需檢視插入程式碼的詳細資訊，請參閱 [/Fx](../../build/reference/fx-merge-injected-code.md) 。 您用於類別的任何基類或介面都會出現在插入的程式碼中。 此外，如果插入的程式碼中預設包含類別，而且您明確地將該類別指定為 coclass 的基底，則屬性提供者將會使用您程式碼中指定的表單。

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
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**可重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
