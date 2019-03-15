---
title: .netmodule 檔做為連結器輸入
ms.date: 11/04/2016
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: fcba363cff567c69ac0fbd0a541953dfe2c8e910
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818098"
---
# <a name="netmodule-files-as-linker-input"></a>.netmodule 檔做為連結器輸入

link.exe 現在接受 MSIL .obj 或 .netmodule 做為輸入。 連結器產生的輸出檔案是組件或.netmodule 任一.obj 或連結器輸入.netmodule 沒有執行階段相依性。

MSVC 編譯器所建立.netmodule [/LN （建立 MSIL 模組）](ln-create-msil-module.md)或使用連結器[/NOASSEMBLY （建立 MSIL 模組）](noassembly-create-a-msil-module.md)。 .obj 一律會建立 Visual c + + 編譯中。 其他 Visual Studio 編譯器中，使用 **/target: module**編譯器選項。

您必須傳遞給連結器.obj 檔案從建立.netmodule 的 Visual c + + 編譯。 因為不再支援傳遞.netmodule **/clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

如需如何叫用連結器，從命令列資訊，請參閱[連結器命令列語法](linking.md)，[使用 MSVC 工具組，從命令列](../building-on-the-command-line.md)，和[設定的路徑和環境變數命令列建置](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

傳遞.netmodule 或.dll 檔給連結器 MSVC 編譯器所編譯 **/clr**可能會導致連結器錯誤。 如需詳細資訊，請參閱 <<c0> [ 選擇.netmodule 輸入檔的格式](choosing-the-format-of-netmodule-input-files.md)。

連結器接受原生.obj 檔案，以及使用編譯的 MSIL.obj 檔 **/clr**。 當在相同的組建中傳遞混合的.obj，產生的輸出檔案的可驗證性，根據預設，會等於輸入模組的可驗證性的最低層級。

如果您目前擁有由兩個或多個組件組成的應用程式，而您要讓應用程式包含在一個組件中，您必須重新編譯組件，然後連結 .obj 或 .netmodule，以產生單一組件。

您必須指定進入點使用[/ENTRY （進入點符號）](entry-entry-point-symbol.md)建立可執行映像時。

當與 MSIL.obj 或.netmodule 檔案連結，使用[/LTCG （連結時間程式碼產生）](ltcg-link-time-code-generation.md)，否則當連結器遭遇 MSIL.obj 或.netmodule，它會重新啟動與 /LTCG 的連結。

MSIL .obj 或 .netmodule 檔案也可以傳遞給 cl.exe。

輸入 MSIL .obj 或 .netmodule 檔案無法具有內嵌資源。 資源內嵌在輸出檔案 （模組或組件） 中使用[與 /ASSEMBLYRESOURCE （內嵌 Managed 資源）](assemblyresource-embed-a-managed-resource.md)連結器選項或使用 **/resource**其他 Visual Studio 編譯器中的編譯器選項。

當執行 MSIL 連結，而且也未指定[/LTCG （連結時間程式碼產生）](ltcg-link-time-code-generation.md)，您會看到告知性訊息報告連結正在重新啟動。 此訊息可以被忽略，但以連結器效能改善 MSIL 連結，明確指定 **/LTCG**。

## <a name="example"></a>範例

在 c + + 程式碼**攔截**相對應的區塊**嘗試**時都會叫用非系統例外狀況。 不過，根據預設，CLR 會包裝與非系統例外狀況<xref:System.Runtime.CompilerServices.RuntimeWrappedException>。 當從 Visual c + + 和非-Visual c + + 模組建立組件，而您想**攔截**中要叫用從其對應的 c + + 程式碼區塊**嘗試**子句時**試**區塊擲回的非系統例外狀況，您必須新增`[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]`屬性設定為非 c + + 模組的原始程式碼。

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

## <a name="example"></a>範例

藉由變更的布林值`WrapNonExceptionThrows`屬性，修改 Visual c + + 程式碼能夠攔截非系統例外狀況。

```cpp
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

## <a name="see-also"></a>另請參閱

- [LINK 輸入檔](link-input-files.md)
- [MSVC 連結器選項](linker-options.md)
