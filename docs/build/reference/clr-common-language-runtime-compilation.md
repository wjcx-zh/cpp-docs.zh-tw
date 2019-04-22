---
title: /clr (Common Language Runtime 編譯)
ms.date: 09/18/2018
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: 1946fdabe66934e64cf95d3c3f12e16bc98ba664
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779348"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Common Language Runtime 編譯)

可讓應用程式和元件使用 Common Language Runtime (CLR) 中的功能。

## <a name="syntax"></a>語法

> **/clr**[**:**_options_]

## <a name="arguments"></a>引數

*options*<br/>
下列一或多個以逗號分隔的參數。

- none

   不含選項中， **/clr**建立應用程式的中繼資料。 中繼資料可供其他 CLR 應用程式使用，並且讓您的應用程式使用其他 CLR 元件之中繼資料內的類型和資料。 如需詳細資訊，請參閱 <<c0> [ 混合 （原生和 Managed） 組件](../../dotnet/mixed-native-and-managed-assemblies.md)。

- **pure**

   **/clr: pure 已被取代**。 Visual Studio 2017 中已移除的選項。 建議您將必須是純 MSIL 的程式碼移植到 C#。

- **Safe.GetTimeOfDay**

   **/clr: safe 已被取代**。 Visual Studio 2017 中已移除的選項。 我們建議您必須是安全的 MSIL，C# 的程式碼移植。

- **noAssembly**

   **已被取代 /clr:noAssembly**。 請改用 [/LN (Create MSIL Module)](ln-create-msil-module.md) 。

   指定不應將組件資訊清單插入輸出檔中。 **noAssembly** 選項預設為非作用中。

   一個在資訊清單中沒有已知為 *模組*的組件中繼資料的 Managed 程式。 **noAssembly** 選項只能用來產生模組。 如果您使用 [/c](c-compile-without-linking.md) 和 **/clr:noAssembly**進行編譯，請在連結器階段中指定 [/NOASSEMBLY](noassembly-create-a-msil-module.md) 選項來建立模組。

   在 Visual C++ 2005 以前， **/clr:noAssembly** 需要 **/LD**。 **/LD** 現在是您指定 **/clr:noAssembly**時意指要使用的項目。

- **initialAppDomain**

   可讓視覺效果C++第 1 版的 clr 上執行的應用程式。  使用 **initialAppDomain** 編譯的應用程式不應由使用 ASP.NET 的應用程式使用，因為它在 CLR 的第 1 版中不受支援。

- **nostdlib**

   指示編譯器忽略預設 \clr 目錄。 如果包含多個版本的 DLL (例如 System.dll)，編譯器會產生錯誤。 使用此選項可讓您指定要在編譯期間使用的特定架構。

## <a name="remarks"></a>備註

Managed 程式碼是可由 CLR 檢查及管理的程式碼。 Managed 程式碼可以存取 Managed 物件。 如需詳細資訊，請參閱 [/clr Restrictions](clr-restrictions.md)。

如需如何開發可定義和使用 Managed 類型之應用程式的相關資訊，請參閱 [Component Extensions for Runtime Platforms](../../extensions/component-extensions-for-runtime-platforms.md)。

使用 **/clr** 編譯的應用程式不一定包含 Managed 資料。

若要啟用偵錯 managed 應用程式上，請參閱[/ASSEMBLYDEBUG (加入 DebuggableAttribute)](assemblydebug-add-debuggableattribute.md)。

只有 CLR 類型會在記憶體回收堆積上具現化。 如需詳細資訊，請參閱 <<c0> [ 類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)。 若要將函式編譯為原生程式碼，請使用 `unmanaged` pragma。 如需詳細資訊，請參閱 < [managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。

**/clr** 預設為非作用中。 當 **/clr** 處於作用中， **/MD** 也會處於作用中。 如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](md-mt-ld-use-run-time-library.md)。 **/MD** 可確保會從標準標頭檔 (.h) 中選取動態連結、多執行緒版本的執行階段常式。 Managed 程式設計需要進行多執行緒處理，因為 CLR 記憶體回收行程會在輔助執行緒中執行完成項。

如果您使用編譯 **/c**，您可以指定與產生之輸出檔的 CLR 型別[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)。

**/clr** 意指要使用 **/EHa**，且沒有其他 **/EH** 選項受 **/clr**支援。 如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](eh-exception-handling-model.md)。

如需如何判斷檔案之 CLR 映像類型的資訊，請參閱 [/CLRHEADER](clrheader.md)。

傳遞至指定連結器之引動過程的所有模組，都必須以相同執行階段程式庫編譯器選項 (**/MD** 或 **/LD**) 進行編譯。

使用 [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) 連結器選項可在組件中內嵌資源。 [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)、 [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)和 [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 連結器選項也可讓您自訂組件的建立方式。

使用 **/clr** 時， `_MANAGED` 符號會定義為 1。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。

原生物件檔中的全域變數會先初始化 (如果可執行檔是 DLL，會在 DllMain 期間執行)，然後初始化 Managed 區段中的全域變數 (在任何 Managed 程式碼執行之前)。 `#pragma` [init_seg](../../preprocessor/init-seg.md)只會影響 managed 與 unmanaged 類別中的初始設定順序。

## <a name="metadata-and-unnamed-classes"></a>中繼資料和未命名的類別

未命名的類別將會出現命名如下的中繼資料內： `$UnnamedClass$`*crc-of-current-file-name*`$`*index*`$`，其中 *index* 是編譯中未命名類別的循序計數。 例如，下列程式碼範例會在中繼資料中產生未命名的類別。

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

使用 ildasm.exe 可檢視中繼資料。

## <a name="see-also"></a>另請參閱

[MSVC 編譯器選項](compiler-options.md)<br/>
[MSVC 編譯器命令列語法](compiler-command-line-syntax.md)
