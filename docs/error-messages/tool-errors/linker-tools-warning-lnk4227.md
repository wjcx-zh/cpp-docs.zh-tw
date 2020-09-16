---
title: 連結器工具警告 LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7ac3ef2b6ad8f05a454dafe5e6a7ea0abc07a066
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685485"
---
# <a name="linker-tools-warning-lnk4227"></a>連結器工具警告 LNK4227

> 中繼資料作業警告 (*HRESULT*) ： *warning_message*

合併時，連結器偵測到中繼資料差異：

- 一或多個參考的元件，以及目前正在建立的元件。

- 編譯中的一或多個原始程式碼檔。

例如，如果您有兩個具有相同名稱的全域函式，但參數資訊宣告不同 (也就是說，宣告在所有 compilands) 中都不一致，可能會導致 LNK4227。 在每個 .obj 檔案上使用 ildasm.exe/TEXT/METADATA *object_file* ，以查看類型的差異。

LNK4227 也可用來報告源自另一個工具的問題。 搜尋警告訊息以取得詳細資訊。

必須修正中繼資料問題才能解決警告。

## <a name="examples"></a>範例

當參考的元件簽章的簽章不同于參考元件的元件時，就會產生 LNK4227。

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

當將錯誤格式的版本號碼傳遞至元件屬性時，也可以產生 LNK4227。  ' * ' 標記法是特有的 `AssemblyVersionAttribute` 。  若要解決這個警告，請只在的版本屬性中使用數位 `AssemblyVersionAttribute` 。

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
