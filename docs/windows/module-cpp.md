---
title: 模組 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.module
dev_langs:
- C++
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac443927c2dcbb00cc01dd3cd63a95441a4a1bf0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711797"
---
# <a name="module-c"></a>module (C++)

在 .idl 檔案中定義程式庫區塊。

## <a name="syntax"></a>語法

```cpp
[ module (
   type=dll,
   name=string,
   version=1.0,
   uuid=uuid,
   lcid=integer,
   control=boolean,
   helpstring=string,
   helpstringdll=string,
   helpfile=string,
   helpcontext=integer,
   helpstringcontext=integer,
   hidden=boolean,
   restricted=boolean,
   custom=string,
   resource_name=string,
) ];
```

### <a name="parameters"></a>參數

*type*  
（選擇性）可以是下列其中一項：

- `dll` 新增函式和類別，可讓產生的 DLL 當成同處理序 COM 伺服器。 這是預設值。

- `exe` 將函式和類別可讓產生可執行檔當成跨處理序 COM 伺服器。

- `service` 將函式和類別可讓產生可執行檔當成 NT 服務。

- `unspecified` 停止插入與模組屬性相關的 ATL 程式碼： 插入 「 ATL 模組類別、 全域執行個體 _AtlModule 和輸入點函式。 因為專案中有其他屬性，所以請不要停止插入 ATL 程式碼。

*name*  
（選擇性）程式庫區塊的名稱。

*version*  
（選擇性）您想要指派給程式庫區塊的版本號碼。 預設值為 1.0。

*uuid*  
程式庫的唯一識別碼。 如果您省略此參數，將會自動產生程式庫的識別碼。 您可能需要擷取*uuid*程式庫區塊，您可以使用識別碼來這麼做 **__uuidof (** *libraryname* **)**。

*lcid*  
當地語系化參數。 請參閱[lcid](/windows/desktop/Midl/lcid)如需詳細資訊。

*control*  
（選擇性）指定媒體櫃中的所有 coclass 的控制項。

*helpstring*  
指定類型程式庫。

*helpstringdll*  
（選擇性）設定用來執行文件字串查閱之.dll 檔案的名稱。 請參閱[helpstringdll](/windows/desktop/Midl/helpstringdll)如需詳細資訊。

*helpfile*  
（選擇性）名稱**協助**型別程式庫的檔案。

*helpcontext*  
（選擇性）**說明 ID**這個類型程式庫。

*helpstringcontext*  
（選擇性）請參閱[helpstringcontext](../windows/helpstringcontext.md)如需詳細資訊。

*hidden*  
（選擇性）避免顯示整個媒體櫃。 此用法是與控制項搭配使用。 主機需要建立新的類型程式庫，以包裝控制項與擴充屬性。 請參閱[隱藏](/windows/desktop/Midl/hidden)MIDL 屬性，如需詳細資訊。

*restricted*  
（選擇性）程式庫成員不能任意呼叫。 請參閱[限制](/windows/desktop/Midl/restricted)MIDL 屬性，如需詳細資訊。

*custom*  
（選擇性）一或多個屬性;這是類似[自訂](../windows/custom-cpp.md)屬性。 第一個參數*自訂*是屬性的 GUID。 例如: 

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*  
.rgs 檔案的字串資源識別碼，用來註冊 DLL、可執行檔或服務的應用程式識別碼。 模組是類型服務時，也可以使用這個引數來取得包含服務名稱之字串的識別碼。

> [!NOTE]
> .rgs 檔案以及包含服務名稱的字串應該包含相同的數值。

## <a name="remarks"></a>備註

除非您指定*受限*參數來[emitidl](../windows/emitidl.md)，**模組**需要使用 c + + 屬性的任何程式中。

除了 **module** 屬性之外，如果原始程式碼同時使用 [dispinterface](../windows/dispinterface.md)、 [dual](../windows/dual.md)、 [object](../windows/object-cpp.md)或表示 [coclass](../windows/coclass.md)的屬性，則會建立程式庫區塊。

一個 .idl 檔案中只允許一個程式庫區塊。 將會合併原始程式碼中的多個模組項目，並實作最新的參數值。

如果在使用 ATL 的專案內使用此屬性，則屬性的行為會變更。 除了上述的行為，屬性也會插入全域物件 (稱為`_AtlModule`) 的正確類型及其他支援程式碼。 如果屬性是獨立的，則會插入從正確模組類型衍生的類別。 如果將屬性套用至類別，則會新增正確模組類型的基底類別。 正確的類型由值決定*型別*參數：

- `type` = **dll**

   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) 是當成基底類別和 COM 伺服器所需的標準 DLL 進入點使用。 這些進入點是[DllMain](/windows/desktop/Dlls/dllmain)， [DllRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms682162)， [DllUnRegisterServer](https://msdn.microsoft.com/library/windows/desktop/ms691457)， [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow)，和[DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891)。

- `type` = **exe**

   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md)當成基底類別和標準可執行檔進入點[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)。

- `type` = **service**

   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md)當成基底類別和標準可執行檔進入點[WinMain](https://msdn.microsoft.com/library/windows/desktop/ms633559)。

- `type` = **unspecified**

   停止插入與 module 屬性相關聯的 ATL 程式碼。

## <a name="example"></a>範例

下列程式碼示範如何在產生的 .idl 檔案中建立程式庫區塊。

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

下列程式碼示範您可以提供自己的函式實作，而函式會出現在因使用 **module**而插入的程式碼中。 如需檢視插入程式碼的詳細資訊，請參閱 [/Fx](../build/reference/fx-merge-injected-code.md) 。 若要覆寫 **module** 屬性所插入的其中一個函式，請建立將包含函式實作的類別，並將 **module** 屬性套用至該類別。

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

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[類別屬性](../windows/class-attributes.md)  
[獨立屬性](../windows/stand-alone-attributes.md)  
[Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)  
[usesgetlasterror](../windows/usesgetlasterror.md)  
[程式庫](/windows/desktop/Midl/library)  
[helpcontext](../windows/helpcontext.md)  
[helpstring](../windows/helpstring.md)  
[helpfile](../windows/helpfile.md)  
[version](../windows/version-cpp.md)  