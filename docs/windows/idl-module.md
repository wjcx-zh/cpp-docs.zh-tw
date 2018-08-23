---
title: idl_module |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7424581c277e7b20132fd5e667acb77a4a95789e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598646"
---
# <a name="idlmodule"></a>idl_module

.Dll 檔中指定的進入點。

## <a name="syntax"></a>語法

```cpp
[ idl_module (
   name=module_name,
   dllname=dll,
   uuid="uuid",
   helpstring="help text",
   helpstringcontext=helpcontextID,
   helpcontext=helpcontext,
   hidden,
   restricted
) ]
function declaration
```

### <a name="parameters"></a>參數

*name*  
會在.idl 檔中的程式碼區塊的使用者定義的名稱。

*dllname* （選擇性）  
包含匯出的.dll 檔案。

*uuid* （選擇性）  
唯一 ID。

*helpstring* （選擇性）  
字元字串，用來描述類型程式庫。

*helpstringcontext* （選擇性）  
.Hlp 或.chm 檔案中的 [說明] 主題的識別碼。

*helpcontext* （選擇性）  
此類型程式庫的說明識別碼。

*隱藏*（選擇性）  
避免程式庫顯示為參數。 如需詳細資訊，請參閱 [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL 屬性。

*限制*（選擇性）  
程式庫成員不能任意呼叫。 如需詳細資訊，請參閱 [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL 屬性。

*函式宣告*  
您將定義的函式。

## <a name="remarks"></a>備註

**Idl_module** c + + 屬性可讓您指定的.dll 檔案，可讓您從.dll 檔案匯入項目點。

**Idl_module**屬性有類似的功能[模組](http://msdn.microsoft.com/library/windows/desktop/aa367099)MIDL 屬性。

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

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[獨立屬性](../windows/stand-alone-attributes.md)  
[entry](../windows/entry.md)  