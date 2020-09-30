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
ms.openlocfilehash: aa5935332cfa12c02e8084136a311a7593a4f3b9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508585"
---
# <a name="marshal_context-class"></a>marshal_context 類別

這個類別會在原生和 Managed 環境之間轉換。

## <a name="syntax"></a>語法

```cpp
class marshal_context
```

## <a name="remarks"></a>備註

為需要內容的資料轉換使用 `marshal_context` 類別。 如需有關需要內容的轉換以及必須包含哪些封送處理檔案的詳細資訊，請參閱 [c + + 中的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。 在您使用內容時的封送處理結果的有效性只到 `marshal_context` 物件終結時。 若要保存結果，您必須複製資料。

`marshal_context`也可以用於許多資料轉換。 以這種方式重複使用內容，並不會影響先前封送處理呼叫的結果。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|`marshal_context`針對 managed 和原生資料類型之間的資料轉換，建立要使用的物件。|
|[marshal_coNtext：： ~ marshal_coNtext](#tilde-marshal-context)|終結 `marshal_context` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。|

## <a name="requirements"></a>需求

**標頭檔：** \<msclr\marshal.h> 、 \<msclr\marshal_windows.h> 、 \<msclr\marshal_cppstd.h> 或 \<msclr\marshal_atl.h>

**命名空間：** msclr：： interop

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a> marshal_coNtext：： marshal_coNtext

`marshal_context`針對 managed 和原生資料類型之間的資料轉換，建立要使用的物件。

```cpp
marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 如需有關哪些翻譯需要內容以及您必須在應用程式中包含哪些封送處理檔案的詳細資訊，請參閱 [c + + 中的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。

### <a name="example"></a>範例

請參閱 [marshal_coNtext：： marshal_as](#marshal-as)的範例。

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a> marshal_coNtext：： ~ marshal_coNtext

終結 `marshal_context` 物件。

```cpp
~marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 請參閱 [c + + 中的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md) ，以取得哪些翻譯需要內容，以及哪些封送處理檔案必須包含在應用程式中的詳細資訊。

刪除 `marshal_context` 物件將會使要由該內容轉換的資料失效。 如果想要在終結 `marshal_context` 物件之後保留資料，您必須手動將資料複製至會保存的變數。

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a> marshal_coNtext：： marshal_as

在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>參數

*input*<br/>
在要封送處理至變數的值 `To_Type` 。

### <a name="return-value"></a>傳回值

型別的變數 `To_Type` ，這是的轉換值 `input` 。

### <a name="remarks"></a>備註

這個函式會在特定資料物件上執行封送處理。 此函數僅適用于在 [c + + 中的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)中，資料表所指出的轉換。

如果您嘗試封送處理一對不支援的資料類型， `marshal_as` 將會在編譯時期產生錯誤 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 。 如需詳細資訊，請閱讀此錯誤所提供的訊息。 `C4996`除了被取代的函式之外，可能會產生錯誤。 產生此錯誤的兩個條件是嘗試封送處理一組不支援的資料類型，並嘗試將其用於 `marshal_as` 需要內容的轉換。

封送處理程式庫包含數個標頭檔。 任何轉換都只需要一個檔案，但如果您需要進行其他轉換，則可以包含其他檔案。 `Marshaling Overview in C++` 中的表格所指出的封送處理檔案應該包含在每次轉換中。

### <a name="example"></a>範例

這個範例會建立從 `System::String` 到 `const char *` 變數類型的封送處理的內容。 已轉換的資料在刪除內容的那一行之後將無法有效。

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
