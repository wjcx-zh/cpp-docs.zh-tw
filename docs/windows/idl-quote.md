---
title: idl_quote |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_quote
dev_langs:
- C++
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a79f731ef0080e38e2c1b60d8e4924a5bf75089e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600291"
---
# <a name="idlquote"></a>idl_quote

可讓您使用目前版本的 Visual c + + 中不支援的 IDL 建構，並將它們傳遞至所產生的.idl 檔案。

## <a name="syntax"></a>語法

```cpp
[ idl_quote(
   text
) ]
```

### <a name="parameters"></a>參數

*文字*  
您想要傳遞至所產生的.idl 檔案而不會傳回編譯器錯誤 Visual c + + 編譯器的屬性名稱。

## <a name="remarks"></a>備註

如果**idl_quote** c + + 屬性當做獨立屬性 （具有後面的分號右括號），然後*文字*放在合併的.idl 檔案原狀。 如果**idl_quote**符號，適用於*文字*會放置在該符號的屬性區塊。

## <a name="example"></a>範例

下列程式碼顯示如何您也可以指定不支援的屬性 (使用**在**，這支援)，以及如何定義及使用未定義的.idl 建構：

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

此程式碼會造成`MYFLOT`並`MYDUB`而*文字*放在產生的.idl 檔中的項目。 *名稱*參數強制*文字*要參考的任何動作之前放置*名稱*產生的.idl 檔案中。 *相依性*參數會強制之前放置的相依性清單定義*文字*產生的.idl 檔案中。

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