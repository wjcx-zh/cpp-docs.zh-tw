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
ms.openlocfilehash: 80aade53bf1d1c9aa30c4b8c8fe59c2247fe3cfb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515783"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

能夠使用 C++ 關鍵字作為識別碼。

## <a name="all-platforms"></a>所有平台

### <a name="syntax"></a>語法

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>備註

允許針對不是關鍵字的識別碼使用 **__identifier** 關鍵字，但就樣式而言，強烈建議不要使用。

## <a name="windows-runtime"></a>Windows 執行階段

### <a name="requirements"></a>需求

編譯器選項：`/ZW`

### <a name="examples"></a>範例

**範例**

在下列範例中，會在 C# 中建立名為 **template** 的類別，並以 DLL 形式散發。 在使用 **template** 類別的 C++/CLI 程式中，**__identifier** 關鍵字會隱藏 **template** 是標準 C++ 關鍵字的事實。

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

**__Identifier** 關鍵字適用於 `/clr` 編譯器選項。

### <a name="requirements"></a>需求

編譯器選項：`/clr`

### <a name="examples"></a>範例

在下列範例中，會在 C# 中建立名為 **template** 的類別，並以 DLL 形式散發。 在使用 **template** 類別的 C++/CLI 程式中，**__identifier** 關鍵字會隱藏 **template** 是標準 C++ 關鍵字的事實。

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

[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)<br/>
[適用於.NET 和 UWP 的元件延伸模組](component-extensions-for-runtime-platforms.md)