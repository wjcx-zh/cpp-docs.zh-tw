---
title: 連結器工具警告 LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: fb657719c69445ce23d36ccf04ac4a14db0955e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352737"
---
# <a name="linker-tools-warning-lnk4227"></a>連結器工具警告 LNK4227

> 中繼資料作業警告 (*HRESULT*): *warning_message*

合併時，連結器偵測到中繼資料的差異：

- 一或多個參考的組件目前正在建置的組件。

- 一或多個原始程式碼檔編譯中。

比方說，LNK4227 可能造成您有兩個全域函式，具有相同名稱但以不同的方式宣告的參數資訊 （也就是宣告不是在所有編譯中都一致）。 使用 ildasm.exe /TEXT /METADATA *object_file*上每個.obj 檔案，若要查看類型有何不同。

LNK4227 也會報告由另一個工具產生的問題。 搜尋警告訊息，如需詳細資訊。

若要解決這個警告，必須修正中繼資料問題。

## <a name="example"></a>範例

參考的組件簽署不同組件參考時，會產生 LNK4227。

下列範例會產生 LNK4227:

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

然後，

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

格式錯誤的版本號碼傳遞至組件屬性時，也可能會產生 LNK4227。  ' *' 表示法是非負數特有`AssemblyVersionAttribute`。  若要解決這個警告，使用只有中的數字的版本屬性以外的其他`AssemblyVersionAttribute`。

下列範例會產生 LNK4227:

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```