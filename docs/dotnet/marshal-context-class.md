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
ms.openlocfilehash: 7fb22754248e66d7a20292af41a8e1b8ba050451
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080025"
---
# <a name="marshal_context-class"></a>marshal_context 類別

這個類別會在原生和 Managed 環境之間轉換。

## <a name="syntax"></a>語法

```cpp
class marshal_context
```

## <a name="remarks"></a>備註

為需要內容的資料轉換使用 `marshal_context` 類別。 如需有關哪些轉換需要內容以及必須包含哪些封送處理檔案的詳細資訊，請參閱[中C++的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。 在您使用內容時的封送處理結果的有效性只到 `marshal_context` 物件終結時。 若要保存結果，您必須複製資料。

相同的 `marshal_context` 可以用於許多資料轉換。 以這種方式重複使用內容，並不會影響先前封送處理呼叫的結果。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|建立 `marshal_context` 物件，以用於 managed 和原生資料類型之間的資料轉換。|
|[marshal_context::~marshal_context](#tilde-marshal-context)|終結 `marshal_context` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。|

## <a name="requirements"></a>需求

**標頭檔：** \<msclr\marshal.h >、\<msclr \ marshal_windows .h >、\<msclr \ marshal_cppstd. h > 或 \<msclr \ marshal_atl >

**命名空間：** msclr：： interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_coNtext：： marshal_coNtext

建立 `marshal_context` 物件，以用於 managed 和原生資料類型之間的資料轉換。

```cpp
marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 如需有關哪些翻譯需要內容，以及哪些封送處理檔案必須包含在應用程式中的詳細資訊，請參閱[中C++的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。

### <a name="example"></a>範例

請參閱[marshal_coNtext：： marshal_as](../dotnet/marshal-context-marshal-as.md)的範例。

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_coNtext：： ~ marshal_coNtext

終結 `marshal_context` 物件。

```cpp
~marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 如需有關哪些翻譯需要內容，以及哪些封送處理檔案必須包含在應用程式中的詳細資訊，請參閱[中C++的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。

刪除 `marshal_context` 物件將會使要由該內容轉換的資料失效。 如果想要在終結 `marshal_context` 物件之後保留資料，您必須手動將資料複製至會保存的變數。

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_coNtext：： marshal_as

在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>參數

*input*<br/>
在要封送處理至 `To_Type` 變數的值。

### <a name="return-value"></a>傳回值

`To_Type` 類型的變數，這是 `input`的轉換值。

### <a name="remarks"></a>備註

這個函式會在特定資料物件上執行封送處理。 只有在[中C++的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)中，才使用此函數搭配資料表所指示的轉換。

如果您嘗試封送處理一對不支援的資料類型，`marshal_as` 會在編譯時期產生錯誤[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 。 如需詳細資訊，請參閱此錯誤所提供的訊息。 不只是已被取代的函式，也可以產生 `C4996` 錯誤。 產生此錯誤的兩個條件是嘗試封送處理一對不支援的資料類型，並嘗試使用 `marshal_as` 進行需要內容的轉換。

封送處理程式庫是由數個標頭檔所組成。 任何轉換只需要一個檔案，但如果您需要進行其他轉換，則可以包含其他檔案。 `Marshaling Overview in C++` 中的表格所指出的封送處理檔案應該包含在每次轉換中。

### <a name="example"></a>範例

這個範例會建立從 `System::String` 到 `const char *` 變數類型的封送處理的內容。 在刪除內容的那一行之後，轉換的資料將會無效。

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