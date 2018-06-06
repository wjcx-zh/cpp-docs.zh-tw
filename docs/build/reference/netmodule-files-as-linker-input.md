---
title: .netmodule 檔作為連結器輸入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb2ab74e8c9d0285b9bec2f9979257d89797022
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704561"
---
# <a name="netmodule-files-as-linker-input"></a>.netmodule 檔做為連結器輸入

link.exe 現在接受 MSIL .obj 或 .netmodule 做為輸入。 連結器所產生的輸出檔案是組件或.netmodule 沒有在任何.obj 或.netmodule 至連結器輸入的執行階段相依。

由 Visual c + + 編譯器，以建立.netmodule [/LN （建立 MSIL 模組）](../../build/reference/ln-create-msil-module.md)或與連結器[/NOASSEMBLY （建立 MSIL 模組）](../../build/reference/noassembly-create-a-msil-module.md)。 .obj 一律會建立在 Visual c + + 編譯中。 對於其他 Visual Studio 編譯器中，使用 **/target: module**編譯器選項。

您必須傳遞至連結器.obj 檔從 Visual c + + 編譯建立.netmodule。 因為傳入.netmodule 已不再支援 **/clr: pure**和 **/clr: safe**編譯器選項都是 Visual Studio 2015 中已被取代，並不支援的 Visual Studio 2017 中。

如需如何叫用連結器，從命令列資訊，請參閱[連結器命令列語法](../../build/reference/linker-command-line-syntax.md)，[命令列上的建置 C/c + + 程式碼](../../build/building-on-the-command-line.md)，和[設定的路徑和環境變數命令列建置](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。

.Netmodule 或.dll 檔案傳遞至連結器所使用 Visual c + + 編譯器編譯 **/clr**可能會導致連結器錯誤。 如需詳細資訊，請參閱[選擇.netmodule 輸入的檔案格式](../../build/reference/choosing-the-format-of-netmodule-input-files.md)。

連結器接受原生.obj 檔案，以及所編譯的 MSIL 的.obj 檔 **/clr**。 將 resxdatanodes 傳遞混合的.obj 相同組建中，產生的輸出檔案的可驗證性，根據預設，會等於輸入模組的可驗證性的最低層級。

如果您目前擁有由兩個或多個組件組成的應用程式，而您要讓應用程式包含在一個組件中，您必須重新編譯組件，然後連結 .obj 或 .netmodule，以產生單一組件。

您必須指定進入點使用[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)建立可執行映像時。

當連結的 MSIL 的.obj 或.netmodule 檔，使用[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)，否則當連結器遇到 MSIL 的.obj 或.netmodule 時，它會重新啟動以 /LTCG 連結。

MSIL .obj 或 .netmodule 檔案也可以傳遞給 cl.exe。

輸入 MSIL .obj 或 .netmodule 檔案無法具有內嵌資源。 資源內嵌在輸出檔案 （模組或組件）[與 /ASSEMBLYRESOURCE （內嵌 Managed 資源）](../../build/reference/assemblyresource-embed-a-managed-resource.md)連結器選項或 **/resource**在其他 Visual Studio 編譯器編譯的編譯器選項。

當執行 MSIL 連結，而且也未指定[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)，您會看到告知性訊息報告正在重新啟動連結。 這則訊息可以被忽略，但若要連結器的效能改善 MSIL 連結，明確指定 **/LTCG**。

## <a name="example"></a>範例

在 c + + 程式碼中**攔截**區塊對應**再試一次**會叫用的非系統例外狀況。 不過，根據預設，CLR 會包裝與非系統例外狀況<xref:System.Runtime.CompilerServices.RuntimeWrappedException>。 當組件從 Visual c + + 和非-Visual c + + 模組建立，而且您想要**攔截**從其對應的叫用 c + + 程式碼中封鎖**再試一次**子句時**再試一次**區塊擲回非系統例外狀況，您必須新增`[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]`屬性設定為非 c + + 模組的原始程式碼。

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

藉由變更的布林值`WrapNonExceptionThrows`屬性修改的 Visual c + + 程式碼來攔截非系統例外狀況的功能。

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

- [LINK 輸入檔](../../build/reference/link-input-files.md)
- [連結器選項](../../build/reference/linker-options.md)
