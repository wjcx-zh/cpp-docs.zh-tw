---
title: idl_quote （C++ COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 4b05da6d237d71e0cc645ad0f626f75ecd85c827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168025"
---
# <a name="idl_quote"></a>idl_quote

可讓您使用目前版本的 Visual C++中不支援的 IDL 結構，並將它們傳遞至產生的 .idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>參數

*text*<br/>
您想要讓 Microsoft C++編譯器傳遞至產生之 .idl 檔案的屬性名稱，而不會傳回編譯器錯誤。

## <a name="remarks"></a>備註

如果**idl_quote** C++屬性當做獨立屬性使用（在右括弧後面加上分號），則會將*文字*放在合併的 .idl 檔案中，如同原狀。 如果在符號上使用**idl_quote** ，*文字*就會放在該符號的屬性區塊內。

## <a name="example"></a>範例

下列程式碼顯示如何指定不支援的屬性（在支援的**中**使用），以及如何定義和使用未定義的 .idl 結構：

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

這段程式碼會導致 `MYFLOT` 和 `MYDUB`，以及將*文字*輸入放在產生的 .idl 檔案中。 *Name*參數會強制將*文字*放在所產生 .idl 檔案中參考*名稱*的任何專案之前。 Dependency*參數會*強制將相依性清單定義放在產生的 .idl 檔案中的*文字*之前。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|任何位置|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[獨立屬性](stand-alone-attributes.md)
