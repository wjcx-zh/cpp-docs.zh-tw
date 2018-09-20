---
title: marshal_context::marshal_as |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc17010ccccc25679918bc02884774f1644dca69
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379127"
---
# <a name="marshalcontextmarshalas"></a>marshal_context::marshal_as

在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。

## <a name="syntax"></a>語法

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>參數

*input*<br/>
[in]您想要封送處理的值`To_Type`變數。

## <a name="return-value"></a>傳回值

類型的變數`To_Type`也就是轉換的值的`input`。

## <a name="remarks"></a>備註

這個函式會在特定資料物件上執行封送處理。 此函式只適用於中的資料表所表示的轉換[Overview of Marshaling c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)。

如果您嘗試封送處理不支援的資料類型的一組`marshal_as`會產生錯誤[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在編譯時期。 閱讀隨附此錯誤，如需詳細資訊的訊息。 `C4996`錯誤可能產生多個只是已被取代的函式。 會產生此錯誤的兩個條件是嘗試封送處理一對不支援的資料類別，以及嘗試為需要內容的轉換使用 `marshal_as`。

封送處理程式庫是由數個標頭檔所組成。 任何轉換必須只有一個檔案，但如果您需要為其他轉換，您可以包含其他檔案。 `Marshaling Overview in C++` 中的表格所指出的封送處理檔案應該包含在每次轉換中。

## <a name="example"></a>範例

這個範例會建立從 `System::String` 到 `const char *` 變數類型的封送處理的內容。 已轉換的資料在刪除內容的行之後將失效。

```
// marshal_context_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   marshal_context^ context = gcnew marshal_context();
   String^ message = gcnew String("Test String to Marshal");
   const char* result;
   result = context->marshal_as<const char*>( message );
   delete context;
   return 0;
}
```

## <a name="requirements"></a>需求

**標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >

**命名空間：** msclr::interop

## <a name="see-also"></a>另請參閱

[C++ 中封送處理的概觀](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_as](../dotnet/marshal-as.md)<br/>
[marshal_context 類別](../dotnet/marshal-context-class.md)