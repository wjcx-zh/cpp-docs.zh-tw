---
title: .netmodule 檔案做為連結器輸入
description: 描述如何使用混合式。obj 和.netmodule 建立 .NET 元件時，做為連結器輸入的檔案。
ms.date: 01/30/2020
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodule files
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
no-loc:
- obj
- netmodule
- clr
- pure
- safe
ms.openlocfilehash: 83eab25624bdb81ba9191e4efe6a774551502ee0
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912820"
---
# <a name="opno-locnetmodule-files-as-linker-input"></a>.netmodule 檔案做為連結器輸入

連結 .exe 接受 MSIL *`.obj`* 和 *`.netmodule`* 檔案作為輸入。 連結器所產生的輸出檔是元件或 *`.netmodule`* 檔案，對於任何輸入至連結器的 *`.obj`* 或 *`.netmodule`* 檔，沒有執行時間相依性。

## <a name="remarks"></a>備註

*`.netmodule`* 檔案是由具有[/LN （建立 msil 模組）](ln-create-msil-module.md)的 MSVC 編譯器，或透過/NOASSEMBLY 的連結器[（建立 msil 模組）](noassembly-create-a-msil-module.md)所建立。 *`.obj`* 檔案一律會在C++編譯中建立。 如需其他 Visual Studio 編譯器，請使用 **/target:module** 編譯器選項。

連結器必須從建立 *`.netmodule`* 的C++編譯中傳遞 *`.obj`* 檔案。 已不再支援傳入 *`.netmodule`* ，因為 **/clr：pure** 和 **/clr：safe** 編譯器選項在 Visual Studio 2015 中已被取代，而在 Visual Studio 2017 和更新版本中不支援。

如需如何從命令列叫用連結器的詳細資訊，請參閱[連結器命令列語法](linking.md)、[從命令列使用 MSVC 工具](../building-on-the-command-line.md)組，以及[設定命令列組建的路徑和環境變數](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

將 *`.netmodule`* 或 *`.dll`* 檔案傳遞至 MSVC 編譯器使用 **/clr** 所編譯的連結器，可能會導致連結器錯誤。 如需詳細資訊，請參閱[選擇netmodule 輸入檔的格式](choosing-the-format-of-netmodule-input-files.md)。

連結器會同時接受以 **/clr** 編譯的原生 *`.obj`* 檔案和 MSIL *`.obj`* 檔案。 您可以在相同的組建中傳遞混合的 *`.obj`* 檔案。 產生的輸出檔預設可驗證性與最低的輸入模組的可驗證性相同。

您可以變更由兩個或多個元件所組成的應用程式，以包含在一個元件中。 重新編譯元件的來源，然後連結 *`.obj`* 檔案或 *`.netmodule`* 檔案，以產生單一元件。

建立可執行映射時，請使用[/ENTRY （進入點符號）](entry-entry-point-symbol.md)指定進入點。

When linking with an MSIL *`.obj`* or *`.netmodule`* file, use [/LTCG (Link-time code generation)](ltcg-link-time-code-generation.md), otherwise when the linker encounters the MSIL *`.obj`* or *`.netmodule`* , it will restart the link with **/LTCG**. You'll see an informational message that the link is restarting. You can ignore this message, but to improve linker performance, explicitly specify **/LTCG**.

MSIL *`.obj`* or *`.netmodule`* files can also be passed to cl.exe.

Input MSIL *`.obj`* or *`.netmodule`* files can't have embedded resources. Embed resources in an output module or assembly file by using the [/ASSEMBLYRESOURCE (Embed a managed resource)](assemblyresource-embed-a-managed-resource.md) linker option. Or, use the **/resource** compiler option in other Visual Studio compilers.

## <a name="examples"></a>範例

In C++ code, the **`catch`** block of a corresponding **`try`** will be invoked for a non-`System` exception. However, by default, the CLR wraps non-`System` exceptions with <xref:System.Runtime.CompilerServices.RuntimeWrappedException>. When an assembly is created from C++ and non-C++ modules, and you want a **`catch`** block in C++ code to be invoked from its corresponding **`try`** clause when the **`try`** block throws a non-`System` exception, you must add the `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` attribute to the source code for the non-C++ modules.

```cpp
// MSIL_linking.cpp
// compile with: /c /clr
value struct V {};

ref struct MCPP {
   static void Test() {
      try {
         throw (gcnew V);
      }
      catch (V ^) {
         System::Console::WriteLine("caught non System exception in C++ source code file");
      }
   }
};

/*
int main() {
   MCPP::Test();
}
*/
```

By changing the `Boolean` value of the `WrapNonExceptionThrows` attribute, you modify the ability of the C++ code to catch a non-`System` exception.

```csharp
// MSIL_linking_2.cs
// compile with: /target:module /addmodule:MSIL_linking.obj
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console
using System.Runtime.CompilerServices;

// enable non System exceptions
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]

class MLinkTest {
   public static void Main() {
      try {
         MCPP.Test();
      }
      catch (RuntimeWrappedException) {
         System.Console.WriteLine("caught a wrapped exception in C#");
      }
   }
}
```

```Output
caught non System exception in C++ source code file
```

## <a name="see-also"></a>請參閱

- [LINK 輸入檔](link-input-files.md)
- [MSVC 連結器選項](linker-options.md)
