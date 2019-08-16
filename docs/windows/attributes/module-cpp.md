---
title: module (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: daa0ae4aea5ff2a1a3312efcf3c39f43b541abf6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514920"
---
# <a name="module-c"></a>module (C++)

在 .idl 檔案中定義程式庫區塊。

## <a name="syntax"></a>語法

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>參數

*type*<br/>
選擇性可以是下列其中一項:

- `dll`加入可讓產生的 DLL 當做同進程 COM 伺服器運作的函式和類別。 這是預設值。

- `exe`新增函式和類別, 讓產生的可執行檔當做進程外 COM 伺服器來運作。

- `service`新增函式和類別, 讓產生的可執行檔當做 NT 服務運作。

- `unspecified`停用與模組屬性相關的 ATL 程式碼插入: 插入 ATL 模組類別、全域實例 _AtlModule 和進入點函式。 因為專案中有其他屬性，所以請不要停止插入 ATL 程式碼。

*name*<br/>
選擇性程式庫區塊的名稱。

*version*<br/>
選擇性您想要指派給程式庫區塊的版本號碼。 預設值為 1.0。

*uuid*<br/>
程式庫的唯一識別碼。 如果您省略此參數，將會自動產生程式庫的識別碼。 您可能需要取得程式庫區塊的*uuid* , 您可以使用識別碼 **__uuidof (** *libraryname* **)** 來執行此動作。

*lcid*<br/>
當地語系化參數。 如需詳細資訊，請參閱 [lcid](/windows/win32/Midl/lcid) 。

*control*<br/>
選擇性指定程式庫中的所有 coclass 都是控制項。

*helpstring*<br/>
指定類型程式庫。

*helpstringdll*<br/>
選擇性設定要用來執行檔字串查詢的 .DLL 檔案名。 如需詳細資訊，請參閱 [helpstringdll](/windows/win32/Midl/helpstringdll) 。

*helpfile*<br/>
選擇性類型程式庫的說明檔名稱。

*helpcontext*<br/>
選擇性此類型程式庫的說明**識別碼**。

*helpstringcontext*<br/>
選擇性如需詳細資訊, 請參閱[helpstringcoNtext](helpstringcontext.md) 。

*hidden*<br/>
選擇性防止顯示整個媒體櫃。 此用法是與控制項搭配使用。 主機需要建立新的類型程式庫，以包裝控制項與擴充屬性。 如需詳細資訊，請參閱 [hidden](/windows/win32/Midl/hidden) MIDL 屬性。

*restricted*<br/>
選擇性無法任意呼叫程式庫的成員。 如需詳細資訊，請參閱 [restricted](/windows/win32/Midl/restricted) MIDL 屬性。

*custom*<br/>
選擇性一或多個屬性;這類似于[自訂](custom-cpp.md)屬性。 *自訂*的第一個參數是屬性的 GUID。 例如：

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
.rgs 檔案的字串資源識別碼，用來註冊 DLL、可執行檔或服務的應用程式識別碼。 模組是類型服務時，也可以使用這個引數來取得包含服務名稱之字串的識別碼。

> [!NOTE]
> .rgs 檔案以及包含服務名稱的字串應該包含相同的數值。

## <a name="remarks"></a>備註

除非您將 *restricted* 參數指定給 [emitidl](emitidl.md)，否則任何使用 C++ 屬性的程式中都需要 **module** 。

除了 **module** 屬性之外，如果原始程式碼同時使用 [dispinterface](dispinterface.md)、 [dual](dual.md)、 [object](object-cpp.md)或表示 [coclass](coclass.md)的屬性，則會建立程式庫區塊。

一個 .idl 檔案中只允許一個程式庫區塊。 將會合併原始程式碼中的多個模組項目，並實作最新的參數值。

如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 除了上述行為之外, 屬性也會插入正確類型的全域物件 (稱為`_AtlModule`) 以及其他支援程式碼。 如果屬性是獨立的，則會插入從正確模組類型衍生的類別。 如果將屬性套用至類別，則會新增正確模組類型的基底類別。 正確的型別取決於*型*別參數的值:

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) 是當成基底類別和 COM 伺服器所需的標準 DLL 進入點使用。 這些進入點是 [DllMain](/windows/win32/Dlls/dllmain)、 [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver)、 [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver)、 [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)和 [DllGetClassObject](/previous-versions//dd797891\(v=vs.85\))。

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) 是當成基底類別和標準可執行檔進入點 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)使用。

- `type` = **service**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) 是當成基底類別和標準可執行檔進入點 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)使用。

- `type` = **unspecified**

   停止插入與 module 屬性相關聯的 ATL 程式碼。

## <a name="example"></a>範例

下列程式碼示範如何在產生的 .idl 檔案中建立程式庫區塊。

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

下列程式碼示範您可以提供自己的函式實作，而函式會出現在因使用 **module**而插入的程式碼中。 如需檢視插入程式碼的詳細資訊，請參閱 [/Fx](../../build/reference/fx-merge-injected-code.md) 。 若要覆寫 **module** 屬性所插入的其中一個函式，請建立將包含函式實作的類別，並將 **module** 屬性套用至該類別。

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[機庫](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)