---
title: 模組(C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: 9d4f9e23aaf182e28930ba3a4462b07533ba9015
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754373"
---
# <a name="module-c"></a>module (C++)

在 .idl 檔案中定義程式庫區塊。

## <a name="syntax"></a>語法

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>參數

*type*<br/>
( 選擇性的 )可以是以下項目之一:

- `dll`添加允許生成的 DLL 充當行程內 COM 伺服器的函數和類。 這是預設值。

- `exe`添加允許生成的可執行檔的函數和類作為進程外 COM 伺服器運行。

- `service`添加允許生成的可執行檔的函數和類作為 NT 服務運行。

- `unspecified`禁用與模組屬性相關的 ATL 代碼的注入:ATL 模組類的注入、全域實例_AtlModule和入口點函數。 因為專案中有其他屬性，所以請不要停止插入 ATL 程式碼。

*name*<br/>
( 選擇性的 )庫塊的名稱。

*version*<br/>
( 選擇性的 )要分配給庫塊的版本號。 預設值為 1.0。

*uuid*<br/>
程式庫的唯一識別碼。 如果您省略此參數，將會自動產生程式庫的識別碼。 您可能需要擷取程式庫區塊的 *uuid* ，做法是使用識別碼 **__uuidof(** *libraryname* **)**。

*lcid*<br/>
當地語系化參數。 如需詳細資訊，請參閱 [lcid](/windows/win32/Midl/lcid) 。

*控制*<br/>
( 選擇性的 )指定庫中的所有子類都是控制項。

*helpstring*<br/>
指定類型程式庫。

*helpstringdll*<br/>
( 選擇性的 )設定 .dll 檔的名稱,以便用於執行文檔字串尋找。 如需詳細資訊，請參閱 [helpstringdll](/windows/win32/Midl/helpstringdll) 。

*說明檔案*<br/>
( 選擇性的 )類型**庫的說明檔**的名稱。

*helpcontext*<br/>
( 選擇性的 )此類型庫**的幫助 ID。**

*helpstringcontext*<br/>
( 選擇性的 )關於詳細資訊,請參閱[說明字串內容](helpstringcontext.md)。

*隱藏*<br/>
( 選擇性的 )防止顯示整個庫。 此用法是與控制項搭配使用。 主機需要建立新的類型程式庫，以包裝控制項與擴充屬性。 如需詳細資訊，請參閱 [hidden](/windows/win32/Midl/hidden) MIDL 屬性。

*限制*<br/>
( 選擇性的 )不能任意調用庫的成員。 如需詳細資訊，請參閱 [restricted](/windows/win32/Midl/restricted) MIDL 屬性。

*自訂*<br/>
( 選擇性的 )一個或多個屬性;這與[自定義](custom-cpp.md)屬性類似。 *要自定義*的第一個參數是屬性的 GUID。 例如：

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

如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 除了上述行為外,該屬性還插入正確類型的全域物件 (稱為`_AtlModule`) 和其他支持代碼。 如果屬性是獨立的，則會插入從正確模組類型衍生的類別。 如果將屬性套用至類別，則會新增正確模組類型的基底類別。 正確的類型由*類型*參數的值確定:

- `type` = **Dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) 是當成基底類別和 COM 伺服器所需的標準 DLL 進入點使用。 這些進入點是 [DllMain](/windows/win32/Dlls/dllmain)、 [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver)、 [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver)、 [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)和 [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)。

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) 是當成基底類別和標準可執行檔進入點 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)使用。

- `type` = **服務**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) 是當成基底類別和標準可執行檔進入點 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)使用。

- `type` = **未指定**

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
|**重複**|否|
|**所需屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[類型定義、枚舉、聯合和結構屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[圖書館](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[說明檔案](helpfile.md)<br/>
[version](version-cpp.md)
