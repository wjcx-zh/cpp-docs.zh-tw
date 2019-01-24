---
title: marshal_context 類別
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- msclr::interop::marshal_context::marshal_as
helpviewer_keywords:
- msclr::marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
ms.openlocfilehash: 25fc2be80ba0e5d8c7f76cee1f22eed4d1bb4fc7
ms.sourcegitcommit: 9813e146a4eb30929d8352872859e8fcb7ff6d2f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805977"
---
# <a name="marshalcontext-class"></a>marshal_context 類別

這個類別會在原生和 Managed 環境之間轉換。

## <a name="syntax"></a>語法

```cpp
class marshal_context
```

## <a name="remarks"></a>備註

為需要內容的資料轉換使用 `marshal_context` 類別。 如需有關哪些轉換需要內容，以及哪些封送處理的檔案必須包含的詳細資訊，請參閱[的 c + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)。 在您使用內容時的封送處理結果的有效性只到 `marshal_context` 物件終結時。 若要保存結果，您必須複製資料。

相同`marshal_context`可以用於多個資料轉換。 重複使用的內容，以這種方式，不會影響從先前封送處理呼叫的結果。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述| 
|---------|-----------| 
|[marshal_context::marshal_context](#marshal-context)|建構`marshal_context`用於 managed 和原生資料類型之間的資料轉換的物件。| 
|[marshal_context::~marshal_context](#tilde-marshal-context)|終結 `marshal_context` 物件。| 

### <a name="public-methods"></a>公用方法

|名稱|描述| 
|---------|-----------| 
|[marshal_context::marshal_as](#marshal-as)|在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。| 


## <a name="requirements"></a>需求

**標頭檔：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >

**命名空間：** msclr::interop

## <a name="marshal-context"></a>marshal_context::marshal_context

建構`marshal_context`用於 managed 和原生資料類型之間的資料轉換的物件。

```cpp
marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 如需詳細資訊，了解哪種轉譯需要內容，以及哪些封送處理檔案必須包含在您的應用程式，請參閱 <<c0> [ 的 c + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)。

### <a name="example"></a>範例

範例，請參閱[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)。


## <a name="tilde-marshal-context"></a>marshal_context::~marshal_context

終結 `marshal_context` 物件。

```cpp
~marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 請參閱[的 c + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)如需有關何種轉譯需要內容，以及哪些封送處理的檔案必須包含在您的應用程式。

刪除 `marshal_context` 物件將會使要由該內容轉換的資料失效。 如果想要在終結 `marshal_context` 物件之後保留資料，您必須手動將資料複製至會保存的變數。

## <a name="marshal-as"></a>marshal_context::marshal_as

在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>參數

*input*<br/>
[in]您想要封送處理的值`To_Type`變數。

### <a name="return-value"></a>傳回值

類型的變數`To_Type`也就是說的轉換的值`input`。

### <a name="remarks"></a>備註

這個函式會在特定資料物件上執行封送處理。 此函式只適用於中的資料表所表示的轉換[的 c + + 中封送處理概觀](../dotnet/overview-of-marshaling-in-cpp.md)。

如果您嘗試封送處理不支援的資料類型的一組`marshal_as`會產生錯誤[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)在編譯時期。 閱讀隨附此錯誤，如需詳細資訊的訊息。 `C4996`錯誤可能產生多個只是已被取代的函式。 產生此錯誤的兩個條件是嘗試封送處理一對不支援的資料類型，然後嘗試使用`marshal_as`轉換需要內容。

封送處理程式庫是由數個標頭檔所組成。 任何轉換必須只有一個檔案，但如果您需要為其他轉換，您可以包含其他檔案。 `Marshaling Overview in C++` 中的表格所指出的封送處理檔案應該包含在每次轉換中。

### <a name="example"></a>範例

這個範例會建立從 `System::String` 到 `const char *` 變數類型的封送處理的內容。 刪除內容的行之後，已轉換的資料不是有效的。

```cpp
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