---
title: .netmodule 檔做為連結器輸入
ms.date: 05/16/2019
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
ms.openlocfilehash: 50a0f0a1ff5f65a7512e8372de2fe5296c866dca
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837431"
---
# <a name="netmodule-files-as-linker-input"></a>.netmodule 檔做為連結器輸入

link.exe 現在接受 MSIL .obj 或 .netmodule 做為輸入。 連結器產生的輸出檔將是組件或 .netmodule，對連結器的任何輸入 .obj 或 .netmodules 沒有執行階段相依性。

.netmodules 是由 MSVC 編譯器搭配 [/LN (建立 MSIL 模組)](ln-create-msil-module.md) 或由連結器搭配 [/NOASSEMBLY (建立 MSIL 模組)](noassembly-create-a-msil-module.md) 所建立。 .objs 一律會在 Visual C++ 編譯中建立。 如需其他 Visual Studio 編譯器，請使用 **/target:module** 編譯器選項。

您需要從建立 .netmodule 的 Visual C++ 編譯中傳遞 .obj 檔給連結器。 我們已不再支援傳遞 .netmodule，因為 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代，而且無法在 Visual Studio 2017 及更新版本中使用。

如需如何從命令列叫用連結器的資訊，請參閱[連結器命令列語法](linking.md)、[從命令列中使用 MSVC 工具組](../building-on-the-command-line.md)及[設定命令列組建的路徑和環境變數](../setting-the-path-and-environment-variables-for-command-line-builds.md)。

傳遞 .netmodule 或 .dll 檔給由 MSVC 編譯器搭配 **/clr** 編譯的連結器可能會產生連結器錯誤。 如需詳細資訊，請參閱[選擇 .netmodule 輸入檔的格式](choosing-the-format-of-netmodule-input-files.md)。

連結器會接受原生 .obj 檔案，以及使用 **/clr** 編譯的 MSIL .obj 檔案。 在相同組建中傳遞混合的 .objs 時，所產生輸出檔案的可驗證性將預設為同等於輸入模組最低層級的可驗證性。

如果您目前擁有由兩個或多個組件組成的應用程式，而您要讓應用程式包含在一個組件中，您必須重新編譯組件，然後連結 .obj 或 .netmodule，以產生單一組件。

建立可執行映像時，您必須使用 [/ENTRY (進入點符號)](entry-entry-point-symbol.md) 來指定進入點。

與 MSIL .obj 或 .netmodule 檔案連結，請使用 [/LTCG (連結時產生程式碼)](ltcg-link-time-code-generation.md)，否則當連結器遭遇 MSIL .obj 或 .netmodule 時，將會重新啟動與 /LTCG 的連結。

MSIL .obj 或 .netmodule 檔案也可以傳遞給 cl.exe。

輸入 MSIL .obj 或 .netmodule 檔案無法具有內嵌資源。 資源會使用 [/ASSEMBLYRESOURCE (內嵌受控資源)](assemblyresource-embed-a-managed-resource.md) 連結器選項或其他 Visual Studio 中的 **/resource** 編譯器選項來內嵌到輸出檔案 (模組或組件)。

當您執行 MSIL 連結，而且未指定 [/LTCG (連結時產生程式碼)](ltcg-link-time-code-generation.md) 時，您會看到回報連結正在重新啟動的告知性訊息。 您可以忽略此訊息，但為了改善執行 MSIL 連結時的連結器效能，應明確指定 **/LTCG**。

## <a name="example"></a>範例

在 C++ 程式碼中，非系統例外狀況會促使叫用對應**嘗試**的**攔截**區塊。 不過，根據預設，CLR 會以 <xref:System.Runtime.CompilerServices.RuntimeWrappedException> 包裝非系統例外狀況。 如果您從 Visual C++ 和非 Visual C++ 模組中建立組件，並且要 C++ 程式碼中的**攔截**區塊在**嘗試**區段擲出非系統例外狀況時，從其對應的**嘗試**子句中加以叫用，則您必須將 `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` 屬性新增至非 C++ 模組的原始碼。

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

藉由變更 `WrapNonExceptionThrows` 屬性的布林值，您可以修改 Visual C++ 程式碼擷取非系統例外狀況的能力。

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
