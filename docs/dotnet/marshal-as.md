---
title: marshal_as
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 6ab4962f18368f0d896f8b7343baf54e8f59ac52
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "70311622"
---
# <a name="marshal_as"></a>marshal_as

這個方法會在原生和 managed 環境之間轉換資料。

## <a name="syntax"></a>語法

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>參數

*input*<br/>
在您想要封送處理到`To_Type`變數的值。

## <a name="return-value"></a>傳回值

類型`To_Type`的變數，其為的轉換`input`值。

## <a name="remarks"></a>備註

這個方法是在原生和 managed 類型之間轉換資料的簡化方式。 若要判斷支援哪些資料類型，請參閱[中C++的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。 某些資料轉換需要內容。 您可以使用[Marshal_coNtext 類別](../dotnet/marshal-context-class.md)來轉換這些資料類型。

如果您嘗試封送處理一對不支援的資料類型， `marshal_as`將會在編譯時期產生錯誤[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 。 如需詳細資訊，請參閱此錯誤所提供的訊息。 不`C4996`只是已被取代的函式，也可以產生此錯誤。 其中一個範例是嘗試封送處理一對不支援的資料類型。

封送處理程式庫是由數個標頭檔所組成。 任何轉換只需要一個檔案，但如果您需要進行其他轉換，則可以包含其他檔案。 若要查看哪些轉換與哪些檔案相關聯，請查看中的`Marshaling Overview`表格。 不論您想要進行何種轉換，命名空間需求一律有效。

如果`System::ArgumentNullException(_EXCEPTION_NULLPTR)`輸入參數為 null 時則會擲回。

## <a name="example"></a>範例

這個範例會從`const char*`封送處理`System::String`至變數類型。

```
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>需求

**標頭檔：** msclr\marshal.h >、 \<msclr\marshal_windows.h >、 \<msclr\marshal_cppstd.h > 或\<msclr\marshal_atl.h > \<

**命名空間：** msclr：： interop

## <a name="see-also"></a>另請參閱

[C++ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context 類別](../dotnet/marshal-context-class.md)
