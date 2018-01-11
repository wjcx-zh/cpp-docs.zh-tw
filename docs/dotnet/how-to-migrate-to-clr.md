---
title: "如何： 移轉至 clr |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
caps.latest.revision: "37"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f38450831ad85a09d3a43173f8febc7841f02c09
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-migrate-to-clr"></a>如何：移轉至 /clr
本主題討論編譯原生程式碼時，會發生的問題**/clr** (請參閱[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)如需詳細資訊)。 **/clr**可讓 Visual c + + 模組，以叫用，並叫用.NET 組件從同時保留與未受管理模組的相容性。 請參閱[混合 （原生和 Managed） 組件](../dotnet/mixed-native-and-managed-assemblies.md)和[原生和.NET 互通性](../dotnet/native-and-dotnet-interoperability.md)如需使用編譯的優點**/clr**。  
  
## <a name="known-issues-compiling-library-projects-with-clr"></a>已知的問題編譯程式庫專案以 /clr  
 編譯程式庫專案時，visual Studio 會包含一些已知的問題**/clr**:  
  
-   您的程式碼可能會查詢在執行階段類型[CRuntimeClass::FromName](../mfc/reference/cruntimeclass-structure.md#fromname)。 不過，如果類型在 MSIL.dll (編譯**/clr**)，呼叫`FromName`可能會發生在受管理的.dll （將不會看到這個問題如果 FromName 呼叫發生後的程式碼具有的靜態建構函式執行之前失敗在此受管理的.dll 檔中執行）。 若要解決這個問題，您可以強制執行受管理的靜態建構函式的建構函式定義中的受管理的.dll、 匯出，以及從原生的 MFC 應用程式叫用。 例如:   
  
    ```  
    // MFC extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## <a name="compile-with-visual-c"></a>使用 Visual c + + 進行編譯  
 使用之前**/clr**上任何模組在您的專案中，第一次編譯和連結您使用 Visual Studio 2010 的原生專案。  
  
 下列步驟中，依序遵循提供的最簡單路徑**/clr**編譯。 請務必編譯及執行您的專案之後每個步驟。  
  
### <a name="versions-prior-to-visual-c-2003"></a>Visual c + + 2003 中之前的版本  
 如果您要從 Visual c + + 2003 中之前的版本升級到 Visual Studio 2010，您可能會看到編譯器錯誤與在 Visual c + + 2003 中增強的 c + + 標準一致性  
  
### <a name="upgrading-from-visual-c-2003"></a>從 Visual c + + 2003年升級  
 搭配 Visual c + + 2003年所建置的專案之前應該也會先編譯而不**/clr**為 Visual Studio 現在增加了 ANSI/ISO 相容性和一些重大變更。 這是可能需要最注意的變更[CRT 中安全性功能](../c-runtime-library/security-features-in-the-crt.md)。 使用 CRT 的程式碼是很可能會產生取代警告。 這些警告可能會隱藏的但移轉至新[安全性增強版本的 CRT 函式](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)最好，因為它們提供更佳的安全性，而且可能會顯示您的程式碼中的安全性問題。  
  
### <a name="upgrading-from-managed-extensions-for-c"></a>從 Managed Extensions for c + + 升級  
 啟動 Visual Studio 2005 中，撰寫使用 Managed Extensions for c + + 程式碼將無法編譯下**/clr**。  
  
## <a name="convert-c-code-to-c"></a>C 程式碼轉換成 c + +  
 雖然 Visual Studio 會編譯 C 檔案，則需要將它們轉換成 c + + for **/clr**編譯。 實際檔名不需要變更;您可以使用**/Tp** (請參閱[/Tc、 /Tp、 /TC、 /TP （指定原始程式檔類型）](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。)請注意，雖然 c + + 原始程式碼檔所需的**/clr**，則不需要重新建構您的程式碼使用物件導向的開發架構。  
  
 C 程式碼是很可能會需要編譯為 c + + 檔案的變更。 C + + 類型安全規則，都是 strict 讓型別轉換必須設為明確轉換 （cast）。 例如，malloc 會傳回 void 的指標，但可以指派給轉換 C 中任何類型的指標：  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 函式指標也是嚴格的型別安全 c + + 中，因此下列 C 程式碼需要修改。 在 c + + 最好建立`typedef`，定義函式指標類型，然後使用該類型轉換函式指標：  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 C + + 也需要函式必須是原型或是完整定義可以參考或叫用。  
  
 C 程式碼中所使用的識別碼剛好是 c + + 中的關鍵字 (例如`virtual`， `new`， `delete`， `bool`， `true`，`false`等等) 必須重新命名。 這通常可以透過簡單的搜尋和取代操作完成。  
  
 最後，而 C 樣式 COM 呼叫需要明確使用 v-table 和`this`指標，c + + 並不會：  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## <a name="reconfigure-project-settings"></a>重新設定專案設定  
 您的專案編譯和執行 Visual Studio 2010 中之後，您就應該建立新專案組態**/clr**而不修改預設組態。 **/clr**與某些編譯器選項不相容，建立個別的設定可讓您建立以原生或 managed 專案。 當**/clr**屬性頁對話方塊中，與不相容的專案設定中選取**/clr**會停用 (並停用的選項不會自動還原如果**/clr**後續未選取，)。  
  
### <a name="create-new-project-configurations"></a>建立新的專案組態  
 您可以使用**複製設定來源**選項[新專案組態對話方塊裡](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be)建立專案組態，根據現有的專案設定。 這樣一次的偵錯組態，另一次發行組態。 後續變更然後會套用至**/clr** -特定組態，又不會更動原始的專案組態。  
  
 使用自訂建置規則的專案可能需要額外注意。  
  
 此步驟會有不同的含意，對於使用 makefile 專案。 在此情況下，可以設定不同的建置目標或特定版本**/clr**編譯可以建立從原始的複本。  
  
### <a name="change-project-settings"></a>變更專案設定  
 **/clr**可以選取在開發環境中的指示[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。 如先前所述，此步驟會自動停用衝突的專案設定。  
  
> [!NOTE]
>  從 Visual c + + 2003 中，升級的 managed 程式庫或 web 服務專案時**/Zl**編譯器選項會新增至**命令列**屬性頁。 這會造成 LNK2001。 移除**/Zl**從**命令列**屬性頁面，即可解決。 請參閱[/Zl （省略預設程式庫名稱）](../build/reference/zl-omit-default-library-name.md)和[使用專案屬性](../ide/working-with-project-properties.md)如需詳細資訊。 或者，您也可以將 msvcrt.lib 和 msvcurt.lib 加入至連結器的**其他相依性**屬性。  
  
 對於使用 makefile 建置專案，不相容的編譯器選項必須停用一次手動**/clr**加入。 請參閱 /[/clr 限制](../build/reference/clr-restrictions.md)與不相容的編譯器選項資訊**/clr**。  
  
### <a name="precompiled-headers"></a>先行編譯標頭檔  
 先行編譯標頭所支援的**/clr**。 不過，如果您只編譯部份與 CPP 檔案**/clr** （編譯為原生 rest） 的某些變更將需要因為先行編譯標頭以產生**/clr**與那些不相容產生不含**/clr**。 此不相容的問題是因為， **/clr**會產生和需要的中繼資料。 編譯模組**/clr**因此，可以不使用先行編譯標頭不包含中繼資料，和非**/clr**模組不能使用包含中繼資料的先行編譯標頭檔案。  
  
 最簡單的方式來編譯的專案，某些模組已編譯之**/clr**是完全停用先行編譯標頭。 （在 [專案屬性頁] 對話方塊中，開啟 [C/c + +] 節點，然後選取先行編譯標頭。 然後建立/使用先行編譯標頭屬性變更為 「 未使用先行編譯標頭 」。）  
  
 不過，特別是針對大型專案，先行編譯標頭提供更好的編譯速度，因此停用此功能不需要這樣做。 在此情況下建議您最好設定**/clr**和非**/clr**使用個別的先行編譯標頭檔。 這可藉由一個步驟中選取多個要編譯的模組**/clr**使用 [方案總管]、 以滑鼠右鍵按一下群組，並選取屬性。 然後變更建立/使用 PCH 透過檔案和先行編譯標頭檔的屬性，以分別使用不同的標頭檔名稱和 PCH 檔案。  
  
## <a name="fixing-errors"></a>修正錯誤  
 編譯**/clr**可能會導致編譯器、 連結器或執行階段錯誤。 本章節討論最常見的問題。  
  
### <a name="metadata-merge"></a>中繼資料合併  
 不同版本的資料型別可能會導致失敗，因為產生兩種類型的中繼資料不符合連結器。 （這通常被導致時有條件地定義類型的成員，但這些條件不相同的使用類型的所有 CPP 檔案。）在此情況下，連結器會失敗，reporting 符號名稱和定義類型的第二個 OBJ 檔的名稱。 通常會很有用旋轉 OBJ 檔案會傳送給連結器，以探索位置的資料類型的另一個版本的順序。  
  
### <a name="loader-lock-deadlock"></a>載入器鎖定死結  
 在 Visual Studio 2010 和更新版本，< 載入器鎖定死結 > 仍可能是因為在舊版中，但卻是具決定性，而且偵測到並在執行階段報告。 請參閱[初始化的混合的組件](../dotnet/initialization-of-mixed-assemblies.md)的詳細的背景、 指引和解決方案。  
  
### <a name="data-exports"></a>資料匯出  
 匯出 DLL 資料很容易發生錯誤，並不建議使用。 這是因為不保證之前已經執行過一些 managed 的 DLL 部分初始化之資料區段的 DLL。 參考中繼資料與[#using 指示詞](../preprocessor/hash-using-directive-cpp.md)。  
  
### <a name="type-visibility"></a>類型可視性  
 原生型別都是預設私用的。 這會導致無法在 DLL 外部可見的原生型別。 解決這個錯誤，藉由新增`public`至這些型別。  
  
### <a name="floating-point-and-alignment-issues"></a>浮點和對齊問題  
 `__controlfp`不支援 common language runtime (請參閱[_control87、 _controlfp、 \__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)如需詳細資訊)。 CLR 會也不會採用[對齊](../cpp/align-cpp.md)。  
  
### <a name="com-initialization"></a>COM 初始化  
 Common Language Runtime 時，會初始化 COM 自動初始化模組 （自動初始化 COM 時它確實為 MTA）。 如此一來，明確地初始化 COM 會產生表示已初始化 COM 的傳回碼。 嘗試明確初始化 COM 使用一個執行緒模型，CLR 已經另一個執行緒模型來初始化 COM 時，可能會導致應用程式失敗。  
  
 Common language runtime COM MTA 為預設的開始。使用[/CLRTHREADATTRIBUTE （設定 CLR 執行緒屬性）](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)來修改這個。  
  
### <a name="performance-issues"></a>效能問題  
 產生為 MSIL 的原生 c + + 方法間接呼叫方法時，您可能會看到效能降低 （虛擬函式呼叫或使用函式指標）。 若要深入了解，請參閱[Double Thunking](../dotnet/double-thunking-cpp.md)。  
  
 從 MSIL 至原生時，您會發現您的工作集大小增加。 這是因為 common language runtime 提供許多功能，以確保程式正確執行。 如果您**/clr**應用程式未正確地執行，您可能想要啟用 C4793 （預設為關閉），請參閱[編譯器警告 （層級 1 和 3） C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)如需詳細資訊。  
  
### <a name="program-crashes-on-shutdown"></a>在關閉程式當機  
 在某些情況下，CLR 可以在關機之前，managed 程式碼完成執行。 使用`std::set_terminate`和`SIGTERM`可能會導致此。 請參閱[signal 常數](../c-runtime-library/signal-constants.md)和[set_terminate](../c-runtime-library/abnormal-termination.md)如需詳細資訊。  
  
## <a name="using-new-visual-c-features"></a>使用 Visual c + + 的新功能  
 之後您的應用程式編譯、 連結和執行，您可以開始使用.NET 功能中使用編譯任何模組**/clr**。 如需詳細資訊，請參閱[執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)。  
  
 如果您使用 Managed Extensions for c + + 時，您可以將轉換程式碼以使用新語法。 如需語法差異的摘要，請參閱[(NOTINBUILD) Managed Extensions for c + + 語法升級檢查清單](http://msdn.microsoft.com/en-us/edbded88-7ef3-4757-bd9d-b8f48ac2aada)。 如需如何 Managed Extensions for c + + 將轉換的詳細資訊，請參閱[C + + /CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)。  
  
 如需.NET 程式設計 Visual c + + 中，請參閱：  
  
-   [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)  
  
## <a name="see-also"></a>請參閱  
 [混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)