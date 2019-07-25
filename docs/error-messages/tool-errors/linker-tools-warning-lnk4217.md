---
title: 連結器工具警告 LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 1301dd53f71c616d7b7af346923a54c42903c9fd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450866"
---
# <a name="linker-tools-warning-lnk4217"></a>連結器工具警告 LNK4217

> '*filename_1*' 中定義的符號 '*symbol*' 已由函式 '*function*' 中的 '*filename_2*' 匯入

已為符號指定[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) , 即使符號是在相同影像的物件檔中定義也一樣。 請移除`__declspec(dllimport)`修飾詞以解決這個警告。

## <a name="remarks"></a>備註

*符號*是在影像中定義的符號名稱。 *函數*是匯入符號的函式。

當您使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項進行編譯時, 不會出現這個警告。

當您嘗試將兩個模組連結在一起時, 也會發生 LNK4217, 相反地, 您應該使用第一個模組的匯入程式庫來編譯第二個模組。

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

然後，

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

嘗試編譯這兩個模組, 如下所示, 會導致 LNK4217:

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

若要修正此錯誤, 請在編譯這兩個檔案之後, 將 tt .obj 傳遞至 lib 以建立 .lib 檔案, 然後將 main .obj 與 tt 連結, 如下所示:

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>另請參閱

[連結器工具警告 LNK4049](linker-tools-warning-lnk4049.md) \
[連結器工具警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)