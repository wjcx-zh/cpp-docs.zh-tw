---
title: progid |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c395a79cc9e0399000278af1a19916c2c83bb10
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209462"
---
# <a name="progid"></a>progid

指定 COM 物件的 ProgID。

## <a name="syntax"></a>語法

```cpp
[ progid(
   name
) ];
```

### <a name="parameters"></a>參數

*name*  
代表物件的 ProgID。

Progid 會提供人類看得懂的版本，用來識別的 COM/ActiveX 物件的類別識別項 (CLSID)。

## <a name="remarks"></a>備註

**Progid** c + + 屬性可讓您指定 COM 物件的 ProgID。 ProgID 的形式*name1.name2.version*。 如果您未指定*版本*ProgID 的預設版本是 1。 如果您未指定*name1.name2*，預設名稱是*classname.classname*。 如果您未指定**progid**和您指定`vi_progid`， *name1.name2*取自`vi_progid`（下一個循序號碼） 和附加的版本。

如果使用的屬性區塊**progid**也不使用**uuid**，編譯器會檢查登錄，以查看**uuid**存在指定**progid**. 如果**progid**未指定，版本 （和 coclass 的名稱，如果建立在 coclass） 將用來產生**progid**。

**progid**意味著`coclass`屬性，也就是如果您指定**progid**，它是與指定的相同項目`coclass`並**progid**屬性。

**Progid**屬性會導致自動註冊指定的名稱下的類別。 產生的.idl 檔案將不會顯示**progid**值。

使用 ATL 的專案中使用這個屬性時，屬性的行為變更。 除了上述的行為，指定具有此屬性的資訊用於`GetProgID`函式，由插入`coclass`屬性。 如需詳細資訊，請參閱 < [coclass](../windows/coclass.md)屬性。

## <a name="example"></a>範例

範例，請參閱[coclass](../windows/coclass.md)範例使用**progid**。

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
[類別屬性](../windows/class-attributes.md)  
[Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)  
[ProgID 的索引鍵](/windows/desktop/com/-progid--key)  
