---
title: idl_module （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: c58997928fb3121c1ab8e277790969a93d9066de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608682"
---
# <a name="idlmodule"></a>idl_module

.Dll 檔中指定的進入點。

## <a name="syntax"></a>語法

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>參數

*name*<br/>
會在.idl 檔中的程式碼區塊的使用者定義的名稱。

*dllname*<br/>
（選擇性）包含匯出的.dll 檔案。

*uuid*<br/>
（選擇性）唯一的識別碼。

*helpstring*<br/>
（選擇性）字元字串，用來描述類型程式庫。

*helpstringcontext*<br/>
（選擇性）.Hlp 或.chm 檔案中的 [說明] 主題的識別碼。

*helpcontext*<br/>
（選擇性）這個類型程式庫說明識別碼。

*hidden*<br/>
（選擇性）避免程式庫顯示為參數。 如需詳細資訊，請參閱 [hidden](/windows/desktop/Midl/hidden) MIDL 屬性。

*restricted*<br/>
（選擇性）程式庫成員不能任意呼叫。 如需詳細資訊，請參閱 [restricted](/windows/desktop/Midl/restricted) MIDL 屬性。

*函式宣告*<br/>
您將定義的函式。

## <a name="remarks"></a>備註

**Idl_module** c + + 屬性可讓您指定的.dll 檔案，可讓您從.dll 檔案匯入項目點。

**Idl_module**屬性有類似的功能[模組](/windows/desktop/Midl/module)MIDL 屬性。

您可以匯出任何項目從 COM 物件，您可以從匯出的.dll 檔案置於的程式庫區塊的.idl 檔中的 DLL 進入點。

您必須使用**idl_module**兩個步驟。 首先，您必須定義的名稱/DLL 組。 然後，當您使用**idl_module**以指定進入點，請指定名稱和任何額外的屬性。

## <a name="example"></a>範例

下列程式碼示範如何使用**idl_module**屬性：

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
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
[獨立屬性](stand-alone-attributes.md)<br/>
[entry](entry.md)