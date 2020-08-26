---
title: 'coclass (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: 12f7af195f2282955cb16c1f38d4e512ca0f86cb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838876"
---
# <a name="coclass"></a>coclass

建立 COM 物件，它可以執行 COM 介面。

## <a name="syntax"></a>語法

```cpp
[coclass]
```

## <a name="remarks"></a>備註

**Coclass** c + + 屬性會將 coclass 結構放在產生的 .idl 檔案中。

定義 coclass 時，您也可以指定 [uuid](uuid-cpp-attributes.md)、 [version](version-cpp.md)、 [執行緒](threading-cpp.md)、 [vi_progid](vi-progid.md)和 [progid](progid.md) 屬性。 如果未指定任何一個，則會產生。

如果有兩個標頭檔包含具有 **coclass** 屬性的類別，但未指定 guid，則編譯器會針對這兩個類別使用相同的 guid，而這會導致 MIDL 錯誤。  因此， `uuid` 當您使用 **coclass**時，應該使用屬性。

**ATL 專案**

當這個屬性在 ATL 專案中的類別或結構定義之前，它：

- 插入程式碼或資料，以支持對象的自動註冊。

- 插入程式碼或資料，以支持對象的 COM class factory。

- 插入程式碼或資料來執行 `IUnknown` ，並將物件設為可供 COM 建立的物件。

具體而言，會將下列基類新增至目標物件：

- [CComCoClass 類別](../../atl/reference/ccomcoclass-class.md) 會提供物件的預設 Class factory 和匯總模型。

- [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md) 具有以 [執行緒](threading-cpp.md) 屬性指定的執行緒模型類別為基礎的範本。 如果 `threading` 未指定屬性，則預設的執行緒模型為「單元」。

- 如果未指定目標物件的[noncreatable](noncreatable.md)屬性，則會新增[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md) 。

最後，任何未使用內嵌 IDL 定義的雙重介面都會取代為對應的 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md) 類別。 如果在內嵌 IDL 中定義雙重介面，則不會修改基底清單中的特定介面。

**Coclass**屬性也可透過插入的程式碼提供下列函式，或以 `GetObjectCLSID` 靜態方法的形式提供給基類 `CComCoClass` ：

- `UpdateRegistry` 註冊目標類別的 class factory。

- `GetObjectCLSID`與註冊相關的也可以用來取得目標類別的 CLSID。

- `GetObjectFriendlyName` 依預設，會傳回格式為 "" 的字串 \<*target class name*> `Object` 。 如果此函式已存在，則不會加入。 將此函式新增至目標類別，以傳回比自動產生的名稱更易記的名稱。

- `GetProgID`與註冊相關的會傳回以 [progid](progid.md) 屬性指定的字串。

- `GetVersionIndependentProgID` 具有與相同的功能 `GetProgID` ，但它會傳回以 [vi_progid](vi-progid.md)指定的字串。

下列與 COM 對應相關的變更會對目標類別進行：

- 針對目標類別所衍生的所有介面，以及 [Com 介面進入點](../../mfc/com-interface-entry-points.md) 屬性所指定的所有專案，或 [匯總](aggregates.md) 屬性所需的專案，會加入 com 對應。

- [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)宏會插入 COM 對應中。

類別的 .idl 檔中所產生的 coclass 名稱將會與類別具有相同的名稱。  例如，若要 `CMyClass` 在用戶端中透過 MIDL 產生的標頭檔，參考下列範例來存取 coclass 的類別識別碼，請使用 `CLSID_CMyClass` 。

## <a name="example"></a>範例

下列程式碼說明如何使用 **coclass** 屬性：

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

下列範例示範如何覆寫出現在 **coclass** 屬性所插入之程式碼中的函式的預設執行。 如需檢視插入程式碼的詳細資訊，請參閱 [/Fx](../../build/reference/fx-merge-injected-code.md) 。 任何您用於類別的基類或介面都會出現在插入的程式碼中。 此外，如果在插入的程式碼中預設包含某個類別，而您明確指定該類別做為 coclass 的基底，屬性提供者將會使用您程式碼中指定的表單。

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

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**, **`struct`**|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)
