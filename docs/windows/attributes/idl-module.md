---
title: 'idl_module (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 651d2e133d7ef08fce48feded1b7a5aff458adb1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845220"
---
# <a name="idl_module"></a>idl_module

指定 .dll 檔中的進入點。

## <a name="syntax"></a>語法

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>參數

*name*<br/>
將會出現在 .idl 檔中的程式碼區塊的使用者定義名稱。

*dllname*<br/>
 (選擇性) 包含匯出的 .dll 檔案。

*uuid*<br/>
 (選擇性的) 唯一的識別碼。

*helpstring*<br/>
 (選擇性) 用來描述類型程式庫的字元字串。

*helpstringcontext*<br/>
 (選擇性) .hlp 或 .chm 檔案中說明主題的識別碼。

*helpcontext*<br/>
 (選擇性) 此類型程式庫的說明識別碼。

*隱藏*<br/>
 (選擇性) 防止顯示程式庫的參數。 如需詳細資訊，請參閱 [hidden](/windows/win32/Midl/hidden) MIDL 屬性。

*限制*<br/>
 (無法任意呼叫程式庫的選擇性) 成員。 如需詳細資訊，請參閱 [restricted](/windows/win32/Midl/restricted) MIDL 屬性。

*函式宣告*<br/>
您將定義的函數。

## <a name="remarks"></a>備註

**Idl_module** c + + 屬性可讓您指定 .dll 檔中的進入點，讓您從 .dll 檔案匯入。

**Idl_module**屬性具有與[module](/windows/win32/Midl/module) MIDL 屬性類似的功能。

您可以藉由在 .idl 檔案的程式庫區塊中放入 DLL 進入點，從可從 .dll 檔案匯出的 COM 物件匯出任何專案。

您必須使用 **idl_module** 的兩個步驟。 首先，您必須定義成對的名稱/DLL。 然後，當您使用 **idl_module** 指定進入點時，請指定名稱和任何其他屬性。

## <a name="example"></a>範例

下列程式碼顯示如何使用 **idl_module** 屬性：

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|任何位置|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)<br/>
[進入](entry.md)
