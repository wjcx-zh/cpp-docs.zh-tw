---
title: .Lib 檔做為連結器輸入
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
ms.openlocfilehash: 0bf791d682b66d9d0da968fb0bfd5229e912e84c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505338"
---
# <a name="lib-files-as-linker-input"></a>.Lib 檔做為連結器輸入

連結可讓您接受 COFF 標準程式庫和 COFF 匯入程式庫，這兩者通常會有擴充功能。 lib。 標準程式庫包含的物件，並且會 LIB 工具來建立。 匯入程式庫包含其他程式匯出的相關資訊，而且會建立由 LINK 建置的程式包含匯出時，或 LIB 工具。 如需使用程式庫來建立標準或匯入程式庫的資訊，請參閱[LIB 參考](../../build/reference/lib-reference.md)。 如需使用連結來建立匯入程式庫的詳細資訊，請參閱[/DLL](../../build/reference/dll-build-a-dll.md)選項。

連結至指定的程式庫，為檔名引數或預設程式庫。 連結解析外部參考，藉由在命令列上指定的程式庫中第一次搜尋，則程式庫以指定的預設[/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)選項，然後在預設程式庫為.obj 檔中。 如果程式庫名稱指定路徑，連結會尋找在該目錄中的程式庫。 如果未指定路徑，連結看起來，從執行連結的目錄中，然後在任何 LIB 環境變數中指定的目錄中，第一次。

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>若要加入.lib 檔做為開發環境中的連結器輸入

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選擇**輸入**中的屬性頁面**連結器**資料夾。

1. 修改**其他相依性**將.lib 檔案新增的屬性。

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>若要以程式設計方式將.lib 檔新增為連結器輸入

- 請參閱[AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx)。

## <a name="example"></a>範例

下列範例示範如何建立及使用.lib 檔。 首先，建置的.lib 檔案：

```cpp
// lib_link_input_1.cpp
// compile by using: cl /LD lib_link_input_1.cpp
__declspec(dllexport) int Test() {
   return 213;
}
```

然後再使用您剛才建立的.lib 檔案中編譯這個範例：

```cpp
// lib_link_input_2.cpp
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp
__declspec(dllimport) int Test();
#include <iostream>
int main() {
   std::cout << Test() << std::endl;
}
```

```Output
213
```

## <a name="see-also"></a>另請參閱

[LINK 輸入檔](../../build/reference/link-input-files.md)<br/>
[連結器選項](../../build/reference/linker-options.md)