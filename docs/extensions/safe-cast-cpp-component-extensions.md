---
title: safe_cast (C++/CLI 和 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 2eb09680ef6e7d1ee90b62eee8c8971fb4963212
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225120"
---
# <a name="safe_cast-ccli-and-ccx"></a>safe_cast (C++/CLI 和 C++/CX)

如果成功，**safe_cast** 作業會傳回指定的運算式作為指定的型別，否則會擲回 `InvalidCastException`。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

### <a name="syntax"></a>語法

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Windows 執行階段

**safe_cast** 可讓您變更指定運算式的型別。 在您完全預期變數或參數可轉換成特定類型的情況下，您可以在不使用 **try-catch** 區塊的情況下使用 **safe_cast**，在開發期間偵測程式設計錯誤。 如需詳細資訊，請參閱[轉換 (C++/CX)](../cppcx/casting-c-cx.md) \(部分機器翻譯\)。

### <a name="syntax"></a>語法

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>參數

*類型識別碼*<br/>
轉換 *expression* 的目標型別。 一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。

*expression*<br/>
一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。

### <a name="remarks"></a>備註

**safe_cast** `InvalidCastException` 如果無法將*運算式*轉換為*類型識別碼*所指定的類型，則 safe_cast 會擲回。若要攔截 `InvalidCastException` ，請指定[/EH （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md)編譯器選項，並使用**try/catch**語句。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="examples"></a>範例

下列程式碼範例示範如何搭配 Windows 執行階段使用 **safe_cast**。

```cpp
// safe_cast_ZW.cpp
// compile with: /ZW /EHsc

using namespace default;
using namespace Platform;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main(Array<String^>^ args) {
   I1^ i1 = ref new X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.
   }
   catch(InvalidCastException^ ic) {
   wprintf(L"Caught expected exception: %s\n", ic->Message);
   }
}
```

```Output
Caught expected exception: InvalidCastException
```

## <a name="common-language-runtime"></a>Common Language Runtime

**safe_cast** 可讓您變更運算式的型別，並產生可驗證的 MSIL 程式碼。

### <a name="syntax"></a>語法

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>參數

*類型識別碼*<br/>
一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。

*expression*<br/>
一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。

### <a name="remarks"></a>備註

運算式 `safe_cast<` *型別識別碼* `>(` *運算式*會 `)` 將運算元*運算式*轉換成型別*id*的物件。

在將接受 **safe_cast** 的大部分位置中，編譯器將接受 [static_cast](../cpp/static-cast-operator.md)。  不過， **safe_cast**保證會產生可驗證的 msil，其中， **`static_cast`** 會產生無法驗證的 msil。  如需可驗證程式碼的詳細資訊，請參閱[純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)和 [Peverify.exe (PEVerify 工具)](/dotnet/framework/tools/peverify-exe-peverify-tool)。

就像一樣 **`static_cast`** ， **safe_cast**會叫用使用者定義的轉換。

如需轉換的詳細資訊，請參閱[轉換運算子](../cpp/casting-operators.md)。

**safe_cast**不會套用 **`const_cast`** （轉換離開 **`const`** ）。

**safe_cast** 位於 cli 命名空間。  如需詳細資訊，請參閱[平台、預設與 cli 命名空間](platform-default-and-cli-namespaces-cpp-component-extensions.md)。

如需 **safe_cast** 的詳細資訊，請參閱：

- [使用/clr 的 C 樣式轉換（c + +/CLI）](c-style-casts-with-clr-cpp-cli.md)

- [作法：在 C++/CLI 中使用 safe_cast](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

其中一個範例是，編譯器不會接受， **`static_cast`** 但會接受**safe_cast**用於不相關介面類別型之間的轉換。  使用 **safe_cast**，編譯器將不會發出轉換錯誤，並將在執行階段上執行檢查以查看是否能進行轉換

```cpp
// safe_cast.cpp
// compile with: /clr
using namespace System;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main() {
   I1^ i1 = gcnew X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type
   }
   catch(InvalidCastException^) {
      Console::WriteLine("Caught expected exception");
   }
}
```

```Output
Caught expected exception
```

## <a name="see-also"></a>另請參閱

[適用于 .NET 和 UWP 的元件擴充功能](component-extensions-for-runtime-platforms.md)
