---
title: 連結器工具警告 LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7b75cff4f03370951245bde1b485d538ffdb4007
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182938"
---
# <a name="linker-tools-warning-lnk4227"></a>連結器工具警告 LNK4227

> 中繼資料作業警告（*HRESULT*）： *warning_message*

連結器在合併時偵測到中繼資料差異：

- 一或多個參考的元件，其中包含目前正在建立的元件。

- 編譯中的一或多個原始程式碼檔。

例如，如果您有兩個具有相同名稱的全域函式，但以不同的方式宣告參數資訊（也就是所有 compilands 中的宣告都不一致），可能會導致 LNK4227。 針對每個 .obj 檔案使用/TEXT/METADATA *object_file* ，以查看這些類型的差異。

LNK4227 也可用來報告源自另一個工具的問題。 如需詳細資訊，請搜尋警告訊息。

必須修正中繼資料問題，才能解決警告。

## <a name="example"></a>範例

當參考的元件以不同于參考它的元件簽章時，就會產生 LNK4227。

下列範例會產生 LNK4227：

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

然後

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

## <a name="example"></a>範例

當格式錯誤的版本號碼傳遞至元件屬性時，也可能會產生 LNK4227。  ' * ' 標記法是 `AssemblyVersionAttribute`特有的。  若要解決這個警告，請只在 `AssemblyVersionAttribute`以外的版本屬性中使用數位。

下列範例會產生 LNK4227：

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
