---
title: 作法：移轉至 -clr
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- upgrading Visual C++ applications, /clr compiler option
- compiling native code [C++]
- interoperability [C++], /clr compiler option
- interop [C++], /clr compiler option
- migration [C++], /clr compiler option
- /clr compiler option [C++], porting to
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
ms.openlocfilehash: 0c21fe585049ebce6383c5d8f673704e7362cd72
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225692"
---
# <a name="how-to-migrate-to-clr"></a>如何：移轉至 /clr

本主題討論使用 **/clr**編譯機器碼時所發生的問題（如需詳細資訊，請參閱[/Clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md) ）。 除了其他原生 c + + 程式碼之外， **/clr**允許原生 c + + 程式碼叫用並從 .net 元件叫用。 如需使用 **/clr**進行編譯之優點的詳細資訊，請參閱[混合（原生和 Managed）元件](../dotnet/mixed-native-and-managed-assemblies.md)和[原生和 .net 互通性](../dotnet/native-and-dotnet-interoperability.md)。

## <a name="known-issues-compiling-library-projects-with-clr"></a>使用/clr 編譯程式庫專案的已知問題

Visual Studio 包含使用 **/clr**編譯程式庫專案時的一些已知問題：

- 您的程式碼可能會在執行時間使用[CRuntimeClass：： FromName](../mfc/reference/cruntimeclass-structure.md#fromname)查詢類型。 不過，如果類型是在 MSIL .dll 中（以 **/clr**編譯），則呼叫 `FromName` 可能會失敗（如果是在 managed .dll 中執行靜態的程式碼之前）（如果 FromName 呼叫在 managed .dll 中執行後發生，則不會看到這個問題）。 若要解決這個問題，您可以藉由在 managed .dll 中定義函式、將其匯出，以及從原生 MFC 應用程式叫用它，來強制結構管理靜態函式。 例如：

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>使用 Visual C++ 進行編譯

在專案的任何模組上使用 **/clr**之前，請先編譯並連結您的原生專案與 Visual Studio 2010。

下列步驟（後面接著順序）提供 **/clr**編譯的最簡單路徑。 在每個步驟之後，請務必編譯並執行您的專案。

### <a name="versions-prior-to-visual-studio-2003"></a>Visual Studio 2003 之前的版本

如果您要從 Visual Studio 2003 之前的版本升級至 Visual Studio 2010，您可能會在 Visual Studio 2003 中看到與增強型 c + + 標準一致性相關的編譯器錯誤

### <a name="upgrading-from-visual-studio-2003"></a>從 Visual Studio 2003 升級

先前以 Visual Studio 2003 建立的專案應該先使用 **/clr**編譯，因為 Visual Studio 現在增加了 ANSI/ISO 合規性和一些重大變更。 可能需要最多注意的變更是[CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。 使用 CRT 的程式碼很可能會產生取代警告。 您可以隱藏這些警告，但最好是遷移至新的[安全性增強版本的 CRT 函式](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)，因為它們提供較佳的安全性，而且可能會顯示您程式碼中的安全性問題。

### <a name="upgrading-from-managed-extensions-for-c"></a>從 Managed Extensions for C++ 升級

從 Visual Studio 2005 開始，以 Managed Extensions for C++ 撰寫的程式碼不會在 **/clr**下編譯。

## <a name="convert-c-code-to-c"></a>將 C 程式碼轉換成 c + +

雖然 Visual Studio 將會編譯 C 檔案，但必須將它們轉換成 c + + 以進行 **/clr**編譯。 實際的檔案名不需要變更;您可以使用 **/tp** （請參閱[/tc、/tp、/tc、/Tp （指定來源檔案類型）](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)）。請注意，雖然 **/clr**需要 c + + 原始程式碼檔案，但不需要重新考慮您的程式碼來使用物件導向的範例。

C 程式碼在編譯為 c + + 檔案時，很可能需要變更。 C + + 型別安全性規則是嚴格的，因此型別轉換必須使用轉換來明確地進行。 例如，malloc 會傳回 void 指標，但是可以透過 cast 指派給 C 中任何類型的指標：

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

函式指標在 c + + 中也是完全安全的類型，因此下列 C 程式碼需要修改。 在 c + + 中，最好是建立 **`typedef`** 定義函式指標類型的，然後使用該類型來轉型函數指標：

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C + + 也要求函式必須是原型或完整定義，才能加以參考或叫用。

在 c 程式碼中，用來做為 c + + 中關鍵字的識別碼（例如 **`virtual`** 、 **`new`** 、 **`delete`** 、 **`bool`** 、 **`true`** 、等 **`false`** ）必須重新命名。 這通常可以透過簡單的搜尋與取代作業來完成。

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>重新設定專案設定

在您的專案編譯並于 Visual Studio 2010 中執行之後，您應該建立 **/clr**的新專案設定，而不是修改預設設定。 **/clr**與某些編譯器選項不相容，而建立不同的設定可讓您將專案建立為原生或受控。 在 [屬性頁] 對話方塊中選取 **/clr**時，會停用與 **/clr**不相容的專案設定（如果後續未選取 **/clr** ，則不會自動還原已停用的選項）。

### <a name="create-new-project-configurations"></a>建立新的專案設定

您可以使用 [**新增專案設定] 對話方塊**中的 [**複製設定**] 選項（[**組建**Configuration Manager 使用中的方案設定] [  >  **Configuration Manager**  >  **Active Solution Configuration**  >  **新增**]），根據現有的專案設定建立專案設定。 針對 Debug 設定執行此動作一次，並針對發行設定進行一次。 接下來的變更只會套用到 **/clr**特定的設定，讓原始專案設定保持不變。

使用自訂群組建規則的專案可能需要特別注意。

針對使用 makefile 的專案，此步驟會有不同的含意。 在此情況下，您可以設定個別的組建目標，或者可以從原始的複本建立 **/clr**編譯的特定版本。

### <a name="change-project-settings"></a>變更專案設定

您可以遵循[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)中的指示，在開發環境中選取 **/clr** 。 如先前所述，此步驟會自動停用衝突的專案設定。

> [!NOTE]
> 從 Visual Studio 2003 升級 managed 程式庫或 web 服務專案時，會將 **/zl**編譯器選項新增至 [**命令列**] 屬性頁。 這會造成 LNK2001。 從 [**命令列**] 屬性頁中移除 **/zl**以解決。 如需詳細資訊，請參閱[/zl （省略預設程式庫名稱）](../build/reference/zl-omit-default-library-name.md)和[設定編譯器和組建屬性](../build/working-with-project-properties.md)。 或者，將 msvcrt.lib 和 msvcurt.lib 新增至連結器的**其他**相依性屬性。

若為以 makefile 建立的專案，則在加入 **/clr**之後，必須手動停用不相容的編譯器選項。 如需與 **/clr**不相容之編譯器選項的詳細資訊，請參閱/[/clr 限制](../build/reference/clr-restrictions.md)。

### <a name="precompiled-headers"></a>先行編譯標頭檔

**/Clr**下支援先行編譯的標頭。 不過，如果您只使用 **/clr**編譯一些 CPP 檔案（將其餘程式編譯為原生），則需要進行一些變更，因為以 **/clr**產生的先行編譯標頭檔與未使用 **/clr**產生的不相容。 這種不相容的原因是 **/clr**產生的事實，而且需要中繼資料。 因此，已編譯 **/clr**的模組可能不會使用不包含中繼資料的先行編譯標頭檔，而且非 **/clr**模組無法使用包含中繼資料的先行編譯標頭檔。

若要編譯專案（其中有些模組是以 **/clr**編譯），最簡單的方式就是完全停用先行編譯的標頭。 （在 [專案屬性頁] 對話方塊中，開啟 [C/c + +] 節點，然後選取 [先行編譯標頭檔]。 然後將 [建立/使用先行編譯標頭檔] 屬性變更為 [不使用先行編譯標頭檔]）。

不過，特別是大型專案時，先行編譯的標頭會提供更好的編譯速度，因此不需要停用這項功能。 在此情況下，最好將 **/clr**和非 **/clr**檔案設定為使用個別的先行編譯標頭檔。 您**可以使用****方案總管**，以滑鼠右鍵按一下群組，然後選取 [屬性]，藉此在一個步驟中完成這項作業。 然後，變更 [透過檔案建立/使用 PCH] 和 [先行編譯頭檔案屬性]，分別使用不同的標頭檔名稱和 PCH 檔案。

## <a name="fixing-errors"></a>修正錯誤

使用 **/clr**進行編譯可能會導致編譯器、連結器或執行階段錯誤。 本節討論最常見的問題。

### <a name="metadata-merge"></a>中繼資料合併

不同版本的資料類型可能會導致連結器失敗，因為針對這兩個類型所產生的中繼資料不相符。 （這通常是因為有條件地定義類型的成員，但使用該類型的所有 CPP 檔案的條件並不相同）。在此情況下，連結器會失敗，只報告符號名稱和類型定義所在之第二個 OBJ 檔案的名稱。 將 OBJ 檔案傳送至連結器的順序，通常會很有用，因為它會探索其他版本資料類型的位置。

### <a name="loader-lock-deadlock"></a>載入器鎖定鎖死

「載入器鎖定鎖死」可能會發生，但具決定性，而且會在執行時間偵測並回報。 如需詳細的背景、指引和解決方案，請參閱[混合元件的初始化](../dotnet/initialization-of-mixed-assemblies.md)。

### <a name="data-exports"></a>資料匯出

匯出 DLL 資料很容易出錯，而且不建議您這麼做。 這是因為在執行 DLL 的某些 managed 部分之前，不保證會初始化 DLL 的資料區段。 參考具有[#using](../preprocessor/hash-using-directive-cpp.md)指示詞的中繼資料。

### <a name="type-visibility"></a>類型可視性

原生類型預設為私用。 這可能會導致原生類型不會顯示在 DLL 外部。 藉由將加入 **`public`** 至這些類型來解決此錯誤。

### <a name="floating-point-and-alignment-issues"></a>浮點和對齊問題

`__controlfp`通用語言執行時間不支援（如需詳細資訊，請參閱[_control87、_controlfp \_ _control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md) ）。 CLR 也不[會遵循。](../cpp/align-cpp.md)

### <a name="com-initialization"></a>COM 初始化

通用語言執行平臺會在模組初始化時自動初始化 COM （當 COM 自動初始化時，它會以 MTA 的方式完成）。 因此，明確初始化 COM 會產生傳回碼，指出 COM 已經初始化。 當 CLR 已經將 COM 初始化為另一個執行緒模型時，嘗試使用一個執行緒模型明確初始化 COM，可能會導致您的應用程式失敗。

通用語言執行時間預設會將 COM 當做 MTA 啟動;使用[/CLRTHREADATTRIBUTE （設定 CLR 執行緒屬性）](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)來修改此。

### <a name="performance-issues"></a>效能問題

當產生給 MSIL 的原生 c + + 方法間接呼叫（虛擬函式呼叫或使用函式指標）時，您可能會看到效能降低。 若要深入瞭解這方面的資訊，請參閱[雙重 Thunking](../dotnet/double-thunking-cpp.md)。

從原生移至 MSIL 時，您會注意到工作集的大小增加。 這是因為 common language runtime 提供許多功能，以確保程式正確執行。 如果您的 **/clr**應用程式未正確執行，您可能會想要啟用 C4793 （預設為關閉），請參閱[編譯器警告（層級1和3） C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)以取得詳細資訊。

### <a name="program-crashes-on-shutdown"></a>關機時程式損毀

在某些情況下，CLR 可以在您的 managed 程式碼完成執行之前關閉。 使用 `std::set_terminate` 和 `SIGTERM` 可能會造成此問題。 如需詳細資訊，請參閱[信號常數](../c-runtime-library/signal-constants.md)和[set_terminate](../c-runtime-library/abnormal-termination.md) 。

## <a name="using-new-visual-c-features"></a>使用新的 Visual C++ 功能

在您的應用程式編譯、連結和執行之後，您就可以開始在任何以 **/clr**編譯的模組中使用 .net 功能。 如需詳細資訊，請參閱[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)。

如需 Visual C++ .NET 程式設計的詳細資訊，請參閱：

- [使用 c + +/CLI 進行 .NET 程式設計（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)

- [執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>另請參閱

[混合（原生和 Managed）元件](../dotnet/mixed-native-and-managed-assemblies.md)
