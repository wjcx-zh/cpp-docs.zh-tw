---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: b63b7f6fe83c7761846d1d0c70de8b1665ad2f22
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641034"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

可讓您使用 c + + 關鍵字當做識別項。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>語法

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>備註

利用 **__identifier**關鍵字的識別項不是關鍵字是允許的但強烈不建議的樣式。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="examples"></a>範例

**範例**

在下列範例中，具名的類別**範本**是在 C# 中建立和散發的 DLL。 在 C + + 使用的 CLI 程式**範本**類別 **_try**關鍵字會隱藏的事實，**範本**是標準的 c + + 關鍵字。

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>備註

**__Identifier**關鍵字是適用於`/clr`編譯器選項。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

在下列範例中，具名的類別**範本**是在 C# 中建立和散發的 DLL。 在 C + + 使用的 CLI 程式**範本**類別 **_try**關鍵字會隱藏的事實，**範本**是標準的 c + + 關鍵字。

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>另請參閱

[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)<br/>
[適用於.NET 和 UWP 的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)