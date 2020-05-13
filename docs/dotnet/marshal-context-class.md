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
ms.openlocfilehash: 110fe4abf7eb90b05e7feef563efa4882bed0fc6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332004"
---
# <a name="marshal_context-class"></a>marshal_context 類別

這個類別會在原生和 Managed 環境之間轉換。

## <a name="syntax"></a>語法

```cpp
class marshal_context
```

## <a name="remarks"></a>備註

為需要內容的資料轉換使用 `marshal_context` 類別。 有關哪些轉換需要上下文以及必須包含哪些封送檔的詳細資訊,請參閱[C++ 中的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)。 在您使用內容時的封送處理結果的有效性只到 `marshal_context` 物件終結時。 若要保存結果，您必須複製資料。

這同樣`marshal_context`可用於許多數據轉換。 以這種方式重用上下文不會影響以前封送調用的結果。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|---------|-----------|
|[marshal_context::marshal_context](#marshal-context)|建構用於`marshal_context`託管數據類型和本機數據類型之間的資料轉換的物件。|
|[marshal_context:*marshal_context](#tilde-marshal-context)|終結 `marshal_context` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|---------|-----------|
|[marshal_context::marshal_as](#marshal-as)|在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。|

## <a name="requirements"></a>需求

**標題檔**\<:msclr_marshal.h>、msclr_marshal_windows.h \< \<>、msclr_marshal_cppstd.h \<> 或 msclr_marshal_atl.h>

**命名空間**:msclr::互通

## <a name="marshal_contextmarshal_context"></a><a name="marshal-context"></a>marshal_context:marshal_context

建構用於`marshal_context`託管數據類型和本機數據類型之間的資料轉換的物件。

```cpp
marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 有關哪些翻譯需要上下文以及必須在應用程式中包括哪些封送檔的詳細資訊,請參閱[C++ 中的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)。

### <a name="example"></a>範例

請參閱[marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md)的範例。

## <a name="marshal_contextmarshal_context"></a><a name="tilde-marshal-context"></a>marshal_context:*marshal_context

終結 `marshal_context` 物件。

```cpp
~marshal_context();
```

### <a name="remarks"></a>備註

某些資料轉換需要封送處理內容。 有關哪些轉換需要上下文以及哪些封送檔必須包含在應用程式中的詳細資訊,請參閱[C++中的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)。

刪除 `marshal_context` 物件將會使要由該內容轉換的資料失效。 如果想要在終結 `marshal_context` 物件之後保留資料，您必須手動將資料複製至會保存的變數。

## <a name="marshal_contextmarshal_as"></a><a name="marshal-as"></a>marshal_context:marshal_as

在特定資料物件上執行封送處理，以便在 Managed 資料類型和原生資料類型之間進行轉換。

```cpp
To_Type marshal_as<To_Type>(
   From_Type input
);
```

### <a name="parameters"></a>參數

*input*<br/>
[在]要封送到`To_Type`變數的值。

### <a name="return-value"></a>傳回值

類型`To_Type`變數,是轉換的值`input`。

### <a name="remarks"></a>備註

這個函式會在特定資料物件上執行封送處理。 僅對C++ 中[封送概述](../dotnet/overview-of-marshaling-in-cpp.md)中的錶指示的轉換使用此功能。

如果嘗試對不支援的資料類型進行封送`marshal_as`, 則在編譯時將生成錯誤[C4996。](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 有關詳細資訊,請閱讀此錯誤附帶的消息。 可以為`C4996`不僅僅是棄用函數生成錯誤。 生成此錯誤的兩個條件嘗試對不支援的數據類型進行封送,並嘗試用於`marshal_as`需要上下文的轉換。

封送庫由多個標頭文件組成。 任何轉換只需要一個檔,但如果需要其他轉換,可以包含其他檔。 `Marshaling Overview in C++` 中的表格所指出的封送處理檔案應該包含在每次轉換中。

### <a name="example"></a>範例

這個範例會建立從 `System::String` 到 `const char *` 變數類型的封送處理的內容。 轉換後的資料在刪除上下文的行後無效。

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
