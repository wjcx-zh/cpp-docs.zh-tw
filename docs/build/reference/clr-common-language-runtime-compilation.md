---
title: "clr （Common Language Runtime 編譯） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
caps.latest.revision: "72"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a867203585a66bd07eb9f95e289557e82e0553a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Common Language Runtime 編譯)
可讓應用程式和元件使用 Common Language Runtime (CLR) 中的功能。  
  
## <a name="syntax"></a>語法  
  
```  
/clr[:options]  
```  
  
## <a name="arguments"></a>引數  
 `options`  
 下列一或多個以逗號分隔的參數。  
  
 **/clr**  
 建立應用程式的中繼資料。 中繼資料可供其他 CLR 應用程式使用，並且讓您的應用程式使用其他 CLR 元件之中繼資料內的類型和資料。  
  
 如需詳細資訊，請參閱  
  
 [混合 （原生和 Managed） 組件](../../dotnet/mixed-native-and-managed-assemblies.md)和  
  
 [How to: Migrate to /clr](../../dotnet/how-to-migrate-to-clr.md)。  
  
 **/clr:pure**  
 產生 Microsoft Intermediate Language (MSIL) - 僅限沒有原生可執行程式碼的輸出檔。 不過，它可以包含編譯為 MSIL 的原生類型。  
  
 如需詳細資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 /clr:pure 已被取代。 編譯器的未來版本可能不支援此選項。 建議您將必須是純 MSIL 的程式碼移植到 C#。  
  
 **/clr:safe**  
 產生純 MSIL (非原生可執行程式碼) 且可驗證的輸出檔。 **/clr:safe** 允許驗證診斷 ([PEVerify Tool (Peverify.exe)](/dotnet/framework/tools/peverify-exe-peverify-tool))。  
  

 /clr:safe 已被取代。 編譯器的未來版本可能不支援此選項。 建議您將必須是純而可驗證的 MSIL 的程式碼移植到 C#。  
  
 **/clr:noAssembly**  
 指定不應將組件資訊清單插入輸出檔中。 **noAssembly** 選項預設為非作用中。  
  
 **noAssembly** 選項已被取代。 請改用 [/LN (Create MSIL Module)](../../build/reference/ln-create-msil-module.md) 。  
  
 一個在資訊清單中沒有已知為 *模組*的組件中繼資料的 Managed 程式。 **noAssembly** 選項只能用來產生模組。 如果您使用 [/c](../../build/reference/c-compile-without-linking.md) 和 **/clr:noAssembly**進行編譯，請在連結器階段中指定 [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) 選項來建立模組。  
  
 在 Visual C++ 2005 以前， **/clr:noAssembly** 需要 **/LD**。 **/LD** 現在是您指定 **/clr:noAssembly**時意指要使用的項目。  
  
 **/clr:initialAppDomain**  
 可讓 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 應用程式在 CLR 的第 1 版上執行。 如果您使用**initialAppDomain**，您可能會看到的一些問題所討論的[BUG： 當您使用時的 AppDomainUnloaded 例外狀況 managed extensions for Visual c + + 元件](http://go.microsoft.com/fwlink/p/?linkid=169465)microsoft支援的網站。  
  
 使用 **initialAppDomain** 編譯的應用程式不應由使用 ASP.NET 的應用程式使用，因為它在 CLR 的第 1 版中不受支援。  
  
 **/clr:nostdlib**  
 指示編譯器忽略預設 \clr 目錄。 如果包含多個版本的 DLL (例如 System.dll)，編譯器會產生錯誤。 使用此選項可讓您指定要在編譯期間使用的特定架構。  
  
## <a name="remarks"></a>備註  
 Managed 程式碼是可由 CLR 檢查及管理的程式碼。 Managed 程式碼可以存取 Managed 物件。 如需詳細資訊，請參閱 [/clr Restrictions](../../build/reference/clr-restrictions.md)。  
  
 如需如何開發可定義和使用 Managed 類型之應用程式的相關資訊，請參閱 [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md)。  
  
 使用 **/clr** 編譯的應用程式不一定包含 Managed 資料。  
  
 若要啟用偵錯 managed 應用程式上，請參閱[/ASSEMBLYDEBUG (加入 DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md)。  
  
 只有 CLR 類型會在記憶體回收堆積上具現化。 如需詳細資訊，請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)。 若要將函式編譯為原生程式碼，請使用 `unmanaged` pragma。 如需詳細資訊，請參閱[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。  
  
 **/clr** 預設為非作用中。 當 **/clr** 處於作用中， **/MD** 也會處於作用中。 如需詳細資訊，請參閱 [/MD、/MT、/LD (使用執行階段程式庫)](../../build/reference/md-mt-ld-use-run-time-library.md)。 **/MD** 可確保會從標準標頭檔 (.h) 中選取動態連結、多執行緒版本的執行階段常式。 Managed 程式設計需要進行多執行緒處理，因為 CLR 記憶體回收行程會在輔助執行緒中執行完成項。  
  
 如果您使用 **/c**進行編譯，您可以使用 [/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md)指定產生之輸出檔的 CLR 類型 (IJW、安全或純粹)。  
  
 **/clr** 意指要使用 **/EHa**，且沒有其他 **/EH** 選項受 **/clr**支援。 如需詳細資訊，請參閱 [/EH (例外狀況處理模型)](../../build/reference/eh-exception-handling-model.md)。  
  
 如需如何判斷檔案之 CLR 映像類型的資訊，請參閱 [/CLRHEADER](../../build/reference/clrheader.md)。  
  
 傳遞至指定連結器之引動過程的所有模組，都必須以相同執行階段程式庫編譯器選項 (**/MD** 或 **/LD**) 進行編譯。  
  
 使用 [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) 連結器選項可在組件中內嵌資源。 [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)、 [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)和 [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 連結器選項也可讓您自訂組件的建立方式。  
  
 使用 **/clr** 時， `_MANAGED` 符號會定義為 1。 如需詳細資訊，請參閱 [Predefined Macros](../../preprocessor/predefined-macros.md)。  
  
 原生物件檔中的全域變數會先初始化 (如果可執行檔是 DLL，會在 DllMain 期間執行)，然後初始化 Managed 區段中的全域變數 (在任何 Managed 程式碼執行之前)。 `#pragma`[init_seg](../../preprocessor/init-seg.md) 只會影響 Managed 與 Unmanaged 類別中的初始設定順序。  
  
 使用 **/clr:safe** 進行編譯，類似於以 C# 之類的語言使用 [/platform:anycpu](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option) 進行編譯。  
  
## <a name="safe-and-pure-images"></a>安全和純映像  
 純映像會使用 CLR 版本的 C 執行階段 (CRT) 程式庫。 但 CRT 是無法驗證的，因此當您使用 **/clr:safe**進行編譯時，將無法使用 CRT。 如需詳細資訊，請參閱 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
 舉例而言，不能出現在純映像中的原生程式碼，包括內嵌組譯碼、 [setjmp](../../c-runtime-library/reference/setjmp.md)和 [longjmp](../../c-runtime-library/reference/longjmp.md)。  
  
 純映像或安全映像的每個進入點都會受到管理。 當您使用 **/clr**進行編譯時，進入點是原生的。 如需詳細資訊，請參閱 [__clrcall](../../cpp/clrcall.md)。  
  
 當您使用 **/clr:safe**進行編譯時，預設的變數是 [appdomain](../../cpp/appdomain.md) ，且不可以是處理序專屬的。 就 **/clr:pure**而言，雖然 **appdomain** 是預設值，您仍可使用 [程序](../../cpp/process.md) 變數。  
  
 當使用 **/clr** 或 **/clr:pure** 所編譯的 32 位元 .exe 檔執行於 64 位元作業系統時，應用程式會在 WOW64 之下執行，而該環境允許 32 位元應用程式執行於 64 位元作業系統上的 32 位元 CLR。 根據預設，使用 **/clr:safe** 編譯的.exe 檔，將會在執行 64 位元作業系統之電腦的 64 位元 CLR 上執行。 (在 32 位元作業系統上，相同的 .exe 檔會在 32 位元 CLR 上執行)。不過，安全的應用程式可以載入 32 位元元件。 在此情況下，執行於作業系統 64 位元支援下的安全映像在載入 32 位元應用程式時將會失敗 (BadFormatException)。 若要確保安全映像在 64 位元作業系統上載入 32 位元映像時仍可繼續執行，您必須使用 [/CLRIMAGETYPE](../../build/reference/clrimagetype-specify-type-of-clr-image.md) 變更中繼資料 (.corflags)，並將其標示為要在 WOW64 下執行。 下列命令列是範例。 (請換成您自己的項目符號。)  
  
 **cl /clr:safe t.cpp /link /clrimagetype:pure /entry:?main@@$$HYMHXZ /subsystem:console**  
  
 如需如何取得裝飾名稱的相關資訊，請參閱 [Decorated Names](../../build/reference/decorated-names.md)。 如需 64 位元目標的詳細資訊，請參閱[設定 Visual c + + 64 位元、 x64 的目標](../../build/configuring-programs-for-64-bit-visual-cpp.md)。 使用純 CLR 程式碼的相關資訊，請參閱[How to： 移轉至 /clr: pure (C + + CLI)](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)和[純粹的和可驗證程式碼 (C + + CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## <a name="metadata-and-unnamed-classes"></a>中繼資料和未命名的類別  
 未命名的類別將會出現命名如下的中繼資料內： `$UnnamedClass$`*crc-of-current-file-name*`$`*index*`$`，其中 *index* 是編譯中未命名類別的循序計數。 例如，下列程式碼範例會在中繼資料中產生未命名的類別。  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 使用 ildasm.exe 可檢視中繼資料。  
  
## <a name="managed-extensions-for-c"></a>Managed Extensions for C++  
 Visual C++ 已不再支援 **/clr:oldsyntax** 選項。 此選項在 Visual Studio 2005 中已被取代。 以 C++ 撰寫 Managed 程式碼的支援語法是 C++/CLI。 如需詳細資訊，請參閱 [Component Extensions for Runtime Platforms](../../windows/component-extensions-for-runtime-platforms.md)。  
  
 如果您有使用 Managed Extensions for C++ 的程式碼，建議您將其移植以使用 C++/CLI 語法。 如需如何移植程式碼的相關資訊，請參閱 [C++/CLI Migration Primer](../../dotnet/cpp-cli-migration-primer.md)。  
  
#### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中設定這個編譯器選項  
  
1.  在 [ **方案總管**] 中，以滑鼠右鍵按一下專案名稱，然後按一下 [ **屬性** ]，以開啟 [ **屬性頁面** ] 對話方塊。  
  
2.  選取 [ **組態屬性** ] 資料夾。  
  
3.  在 [ **一般** ] 屬性頁面上，修改 [ **Common Language Runtime 支援** ] 屬性。  
  
    > [!NOTE]
    >  如果在 [ **屬性頁面** ] 對話方塊中啟用 **/clr** ，將也會視需要調整與 **/clr** 不相容的編譯器選項屬性。 例如，如果設定了 **/RTC** ，然後啟用 **/clr** ， **/RTC** 將會關閉。  
    >   
    >  此外，當您偵錯 **/clr** 應用程式時，請將 [ **偵錯工具類型** ] 屬性設為 [ **混合** ] 或 [ **僅限 Managed**]。 如需詳細資訊，請參閱[c + + 偵錯組態的專案設定](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)。  
  
     如需如何建立模組，請參閱[/NOASSEMBLY （建立 MSIL 模組）](../../build/reference/noassembly-create-a-msil-module.md)。  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)