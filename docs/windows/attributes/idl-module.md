---
title: idl_module (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 8838a833552ae7066dbcf17b4f676d6626c069f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514669"
---
# <a name="idl_module"></a>idl_module

指定 .dll 檔案中的進入點。

## <a name="syntax"></a>語法

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>參數

*name*<br/>
將出現在 .idl 檔案中之程式碼區塊的使用者定義名稱。

*dllname*<br/>
選擇性包含匯出的 .dll 檔案。

*uuid*<br/>
選擇性唯一識別碼。

*helpstring*<br/>
選擇性用來描述類型程式庫的字元字串。

*helpstringcontext*<br/>
選擇性.Hlp 或 .chm 檔案中說明主題的識別碼。

*helpcontext*<br/>
選擇性此類型程式庫的說明識別碼。

*hidden*<br/>
選擇性防止顯示媒體櫃的參數。 如需詳細資訊，請參閱 [hidden](/windows/win32/Midl/hidden) MIDL 屬性。

*restricted*<br/>
選擇性無法任意呼叫程式庫的成員。 如需詳細資訊，請參閱 [restricted](/windows/win32/Midl/restricted) MIDL 屬性。

*函式宣告*<br/>
您將定義的函數。

## <a name="remarks"></a>備註

**Idl_module** C++屬性可讓您指定 .dll 檔案中的進入點, 這可讓您從 .dll 檔案匯入。

**Idl_module**屬性具有類似[模組](/windows/win32/Midl/module)MIDL 屬性的功能。

您可以藉由將 DLL 進入點放在 .idl 檔案的程式庫區塊中, 從您可以從 .dll 檔案匯出的 COM 物件匯出任何專案。

您必須透過兩個步驟來使用**idl_module** 。 首先, 您必須定義名稱/DLL 配對。 然後, 當您使用**idl_module**指定進入點時, 請指定名稱和任何其他屬性。

## <a name="example"></a>範例

下列程式碼顯示如何使用**idl_module**屬性:

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