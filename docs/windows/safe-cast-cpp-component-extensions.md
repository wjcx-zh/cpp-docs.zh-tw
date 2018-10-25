---
title: safe_cast (C + + /cli 和 C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b8f9b1e40deadbc23fe19f02bf2aaef899c52a6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056690"
---
# <a name="safecast-ccli-and-ccx"></a>safe_cast (C + + /cli 和 C + + /CX)

**Safe_cast**作業會傳回與指定的類型，指定的運算式，如果成功; 否則會擲回`InvalidCastException`。

## <a name="all-runtimes"></a>所有執行階段

(這個語言功能沒有適用所有執行階段的備註。)

### <a name="syntax"></a>語法

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Windows 執行階段

**safe_cast**可讓您變更指定運算式的類型。 在您完全預期變數或參數可轉換成特定類型的情況下，您可以使用**safe_cast**不含**try / catch**區塊，以在開發期間偵測程式設計錯誤。 如需詳細資訊，請參閱 <<c0> [ 轉型 (C + + /CX)](https://msdn.microsoft.com/library/windows/apps/hh755802.aspx)。

### <a name="syntax"></a>語法

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>參數

*類型識別碼*<br/>
要轉換的型別*運算式*到。 一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。

*運算式*<br/>
一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。

### <a name="remarks"></a>備註

**safe_cast**會擲回`InvalidCastException`如果它無法轉換*運算式*所指定的型別*型別 id*。若要攔截`InvalidCastException`，指定[/EH （例外狀況處理模型）](../build/reference/eh-exception-handling-model.md)編譯器選項，並使用**try/catch**陳述式。

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="examples"></a>範例

下列程式碼範例示範如何使用**safe_cast**與 Windows 執行階段。

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

**safe_cast**可讓您變更運算式的類型，並產生可驗證的 MSIL 程式碼。

### <a name="syntax"></a>語法

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>參數

*類型識別碼*<br/>
一個控制代碼，可用來參考或值類型、值類型，或參考或值類型的追蹤參考。

*運算式*<br/>
一個運算式，可針對用來參考或值類型、值類型，或參考或值類型的追蹤參考之控制代碼進行評估。

### <a name="remarks"></a>備註

運算式`safe_cast<`*型別 id*`>(`*運算式*`)`轉換運算元*運算式*物件的型別*型別 id*。

編譯器會接受[static_cast](../cpp/static-cast-operator.md)在大多數的地方，它會接受**safe_cast**。  不過， **safe_cast**保證能夠產生可驗證的 MSIL，其中**static_cast**可能會產生無法驗證的 MSIL。  請參閱[純粹的和可驗證程式碼 (C + + /cli CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)並[Peverify.exe （PEVerify 工具）](/dotnet/framework/tools/peverify-exe-peverify-tool)如需有關驗證的程式碼。

像是**static_cast**， **safe_cast**叫用使用者定義的轉換。

如需有關轉換的詳細資訊，請參閱 <<c0> [ 轉型運算子](../cpp/casting-operators.md)。

**safe_cast**不會套用**const_cast** (拋棄**const**)。

**safe_cast**位於 cli 命名空間。  請參閱[Platform、 default 和 cli 命名空間](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)如需詳細資訊。

如需詳細資訊**safe_cast**，請參閱：

- [使用 /clr 進行 C-style 轉換 (C + + /cli CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)

- [如何：在 C++/CLI 中使用 safe_cast](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

一個範例中的編譯器會接受**static_cast**但接受**safe_cast**是不相關的介面型別之間的轉換。  具有**safe_cast**，編譯器不會發出轉換錯誤，並會執行檢查，以在執行階段，以查看是否可以轉型

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

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)
