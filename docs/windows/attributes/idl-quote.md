---
title: 'idl_quote (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 1d0aa80f64593ed347720b84e4059a0c32dce4be
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844232"
---
# <a name="idl_quote"></a>idl_quote

可讓您使用目前版本的 Visual C++ 不支援的 IDL 結構，並將它們傳遞至產生的 .idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>參數

*text*<br/>
您希望 Microsoft c + + 編譯器傳遞給產生的 .idl 檔案的屬性名稱，而不會傳回編譯器錯誤。

## <a name="remarks"></a>備註

如果使用 **idl_quote** c + + 屬性做為獨立屬性 (在右括弧) 之後有分號，則會將 *文字* 放在合併的 .idl 檔案中。 如果在符號上使用 **idl_quote** ，則會將 *文字* 放在該符號的屬性區塊內。

## <a name="example"></a>範例

下列程式碼將示範如何使用 **in**來指定不支援的屬性 (，這是支援的) 以及如何定義和使用未定義的 .idl 結構：

```cpp
// cpp_attr_ref_idl_quote.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];

[export]
struct MYFLOT {
   int i;
};

[export]
struct MYDUB {
   int i;
};

[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];

typedef struct _S1_TYPE {
   long l1;

union {
   MYFLOT f1; MYDUB d2; } U1_TYPE;
} S1_TYPE;

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]
__interface IStatic{
   HRESULT Func1([idl_quote("in")] int i);
   HRESULT func( S1_TYPE* myStruct );
};
```

此程式碼會使 `MYFLOT` 和 `MYDUB` 和 *文字* 專案放在產生的 .idl 檔案中。 *Name*參數會強制在產生的 .idl 檔案中參考*名稱*的任何內容之前放置*文字*。 Dependency *參數會* 強制將相依性清單定義放在產生的 .idl 檔案中的 *文字* 之前。

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
[獨立屬性](stand-alone-attributes.md)
