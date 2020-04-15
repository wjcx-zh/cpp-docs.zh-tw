---
title: 如何：移轉至 -clr
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
ms.openlocfilehash: 339b1f3172d8b82ece3e98f117f53ed399cbd4e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376072"
---
# <a name="how-to-migrate-to-clr"></a>如何：移轉至 /clr

本主題討論使用 **/clr**編譯本機代碼時出現的問題(有關詳細資訊,請參閱[/clr(通用語言運行時編譯)。](../build/reference/clr-common-language-runtime-compilation.md) **/clr**允許本機C++代碼調用和調用從 .NET 程式集以及其他本機C++代碼。 有關使用 **/clr**編譯的優勢的詳細資訊,請參閱[混合(本機和託管)程式集](../dotnet/mixed-native-and-managed-assemblies.md)以及[本機和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)。

## <a name="known-issues-compiling-library-projects-with-clr"></a>使用 /clr 編譯函式庫專案的已知問題

可視化工作室包含一些已知問題,在編譯庫專案與 **/clr**:

- 您的程式碼可能會在執行時使用[CRuntimeClass 查詢類型::fromName](../mfc/reference/cruntimeclass-structure.md#fromname)。 但是,如果類型位於 MSIL .dll 中(使用 **/clr**`FromName`編譯),則調用 調用可能會失敗,如果它發生在靜態構造函數在託管 .dll 中運行之前(如果 FromName 調用是在託管 .dll 中執行代碼之後發生的,則調用 該調用可能會失敗。 要解決此問題,可以通過在託管 .dll 中定義函數、匯出函數並從本機 MFC 應用程式調用它來強制構造託管靜態構造函數。 例如：

    ```
    // MFC extension DLL Header file:
    __declspec( dllexport ) void EnsureManagedInitialization () {
       // managed code that won't be optimized away
       System::GC::KeepAlive(System::Int32::MaxValue);
    }
    ```

## <a name="compile-with-visual-c"></a>使用視覺化C++編譯

在專案中的任何模組上使用 **/clr**之前,請首先編譯本機專案並將其連結到 Visual Studio 2010。

以下步驟(按順序執行)提供了 **/clr**編譯的最簡單路徑。 在每個步驟之後編譯和運行專案非常重要。

### <a name="versions-prior-to-visual-studio-2003"></a>Visual Studio 2003 之前的版本

如果要從 Visual Studio 2003 之前的版本升級到 Visual Studio 2010,您可能會在 Visual Studio 2003 中看到與增強C++標準符合性相關的編譯器錯誤

### <a name="upgrading-from-visual-studio-2003"></a>從視覺工作室升級 2003

以前使用 Visual Studio 2003 構建的專案也應首先在沒有 **/clr**的情況下編譯,因為 Visual Studio 現在提高了 ANSI/ISO 合規性和一些重大更改。 可能需要最關注的變更是[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。 使用CRT的代碼極可能生成棄用警告。 這些警告可以被抑制,但遷移到[新的CRT函數的安全增強版本](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)是首選,因為它們提供更好的安全性,並可能揭示代碼中的安全問題。

### <a name="upgrading-from-managed-extensions-for-c"></a>從託管擴展升級C++

從 Visual Studio 2005 開始,使用託管擴展編寫的 C++代碼將不會在 **/clr**下編譯。

## <a name="convert-c-code-to-c"></a>將 C 程式碼轉換為C++

儘管 Visual Studio 將編譯 C 檔,但有必要將它們轉換為**C++ 以進行 /clr**編譯。 不需要更改實際的檔名;您可以使用 **/Tp(** 請參考[/Tc、/Tp、/TC、/TP、/TP(指定來源檔案型態))](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)請注意,雖然 C++ 原始程式碼檔是 **/clr**所必需的,但不必重新考慮代碼以使用面向物件的範例。

當編譯為C++檔時,C 代碼很可能需要更改。 C++類型安全規則很嚴格,因此必須使用強制轉換顯式進行類型轉換。 例如,malloc 傳回 void指標,但可以分配給具有強制轉換的 C 中任何類型的指標:

```
int* a = malloc(sizeof(int));   // C code
int* b = (int*)malloc(sizeof(int));   // C++ equivalent
```

函數指標在C++中也嚴格類型安全,因此以下C代碼需要修改。 在C++最好建立定義函式指標型態的,`typedef`然後使用該類型對函數指標進行強制轉換:

```
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code
typedef int(*MYPROC)(int);   // C++ equivalent
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );
```

C++還要求在引用或調用函數之前,對函數進行原型設計或完全定義。

C 代碼中使用的標識碼恰好是C++中的關鍵字(如**虛擬**、**新**、**刪除**、**布爾**、**真**、**假**等)必須重新命名。 這通常可以通過簡單的搜索和替換操作來完成。

```
COMObj1->lpVtbl->Method(COMObj, args);  // C code
COMObj2->Method(args);  // C++ equivalent
```

## <a name="reconfigure-project-settings"></a>重新設定項目設定

在 Visual Studio 2010 中編譯和運行專案後,應為 **/clr**創建新的專案配置,而不是修改預設配置。 **/clr**與某些編譯器選項不相容,創建單獨的配置允許您將專案構建為本機或託管。 在屬性頁對話框中選擇 **/clr**時,將禁用與 **/clr**不相容的專案設置(如果隨後未選中 **/clr,** 則不會自動還原禁用選項)。

### <a name="create-new-project-configurations"></a>建立新項目設定

您可以使用 **「新增專案設定」對話框**中的 **「從複製設定」** 選項(**產生** > **設定管理器** > **活動解決方案配置** > **New)** 來基於現有專案設定創建專案設定。 對於調試配置執行此操作一次,對發佈配置執行一次。 然後,後續更改只能應用於 **/clr**特定配置,保持原始專案配置不變。

使用自定義生成規則的專案可能需要格外注意。

此步驟對使用 makefiles 的專案具有不同的含義。 在這種情況下,可以配置單獨的生成目標,也可以從原始副本創建特定於 **/clr**編譯的版本。

### <a name="change-project-settings"></a>變更項目設定

**/clr**可以按照[/clr(通用語言運行時編譯)](../build/reference/clr-common-language-runtime-compilation.md)中的說明在開發環境中選擇。 如前所述,此步驟將自動禁用衝突的項目設置。

> [!NOTE]
> 從 Visual Studio 2003 升級託管庫或 Web 服務專案時 **,/Zl**編譯器選項將添加到**命令列**屬性頁。 這將導致 LNK2001。 從**命令列**屬性頁中刪除 **/Zl**以進行解析。 有關詳細資訊[,請參閱 /Zl(Omit 預設庫名稱)](../build/reference/zl-omit-default-library-name.md)和[設定編譯器和產生屬性](../build/working-with-project-properties.md)。 或者,將 msvcrt.lib 和 msvcmrt.lib 添加到連結器的附加**依賴項**屬性。

對於使用 makefile 生成的專案,在添加 **/clr**後,必須手動禁用不相容的編譯器選項。 有關與 **/clr**不相容的編譯器選項的資訊,請參閱[/ clr 限制](../build/reference/clr-restrictions.md)。

### <a name="precompiled-headers"></a>先行編譯標頭檔

在 **/clr**下支援預編譯標頭。 但是,如果您只編譯一些使用 **/clr**的 CPP 檔(將其餘檔編譯為本機),則需要進行一些更改,因為使用 **/clr**生成的預編譯標頭與在沒有 **/clr**時生成的標頭不相容。 這種不相容是由於 **/clr**生成和需要元數據。 因此,編譯的**模組 /clr**不能使用不包含元數據的預編譯標頭,並且非 **/clr**模組不能使用包含元數據的預編譯標頭檔。

編譯某些模組編譯 **/clr**的專案的最簡單方法是完全禁用預編譯標頭。 (在項目屬性頁對話框中,打開 C/C++ 節點,然後選擇預編譯標頭。 然後,將"創建/使用預編譯標頭"屬性更改為"不使用預編譯標頭」。。

但是,特別是對於大型項目,預編譯標頭提供了更好的編譯速度,因此禁用此功能是不可取的。 在這種情況下,最好將 **/clr**和非 **/clr**檔配置為使用單獨的預編譯標頭。 這可以通過多選擇要使用**解決方案資源管理器**編譯**的模組/clr、** 右鍵單擊組以及選擇屬性來分一步完成。 然後更改「透過檔案建立/使用 PCH」和「預編譯的標頭檔」屬性,分別使用不同的標頭檔名和 PCH 檔。

## <a name="fixing-errors"></a>修復錯誤

使用 **/clr**編譯可能會導致編譯器、連結器或運行時錯誤。 本節討論最常見的問題。

### <a name="metadata-merge"></a>中繼資料合併

數據類型的不同版本可能導致連結器失敗,因為為兩種類型生成的元數據不匹配。 (這通常是在有條件地定義類型成員時造成的,但對於使用該類型的所有 CPP 檔的條件不同。在這種情況下,連結器失敗,僅報告符號名稱和定義類型的第二個 OBJ 檔的名稱。 旋轉將 OBJ 檔發送到連結器的順序以發現數據類型的其他版本的位置通常很有用。

### <a name="loader-lock-deadlock"></a>載入鎖定鎖定

可能發生「載入程式鎖死鎖」,但具有確定性,並在運行時檢測到並報告。 有關詳細的背景、指導和解決方案,請參閱[混合程式集的初始化](../dotnet/initialization-of-mixed-assemblies.md)。

### <a name="data-exports"></a>資料匯出

匯出 DLL 數據容易出錯,不建議匯出數據。 這是因為 DLL 的數據部分不保證在 DLL 的某些託管部分執行之前進行初始化。 具有[#using指令](../preprocessor/hash-using-directive-cpp.md)的引用元數據。

### <a name="type-visibility"></a>類型可視性

默認情況下,本機類型是私有的。 這可能導致本機類型在 DLL 之外不可見。 通過添加到`public`這些類型來解決此錯誤。

### <a name="floating-point-and-alignment-issues"></a>浮點和對齊問題

`__controlfp`公共語言運行時不支援(有關詳細資訊[,請參閱_control87、_controlfp、_control87_2)。 \_ ](../c-runtime-library/reference/control87-controlfp-control87-2.md) CLR 也不會尊重[對齊](../cpp/align-cpp.md)。

### <a name="com-initialization"></a>COM 初始化

當模組初始化時,通用語言運行時會自動初始化 COM(當 COM 自動初始化時,它作為 MTA 進行初始化)。 因此,顯式初始化 COM 會產生返回代碼,指示 COM 已初始化。 當 CLR 已經將 COM 初始化到另一個線程模型時,嘗試使用一個線程模型顯式初始化 COM 可能會導致應用程式失敗。

默認情況下,通用語言運行時將 COM 作為 MTA 啟動;使用[/CLRTHREADATTRIBUTE(設置 CLR 線程屬性)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md)來修改此。

### <a name="performance-issues"></a>效能問題

當間接調用生成到 MSIL 的本機 C++方法(虛擬函數調用或使用函數指標)時,您可能會看到效能下降。 要瞭解有關此點的更多,請參閱[雙湯。](../dotnet/double-thunking-cpp.md)

從本機移動到 MSIL 時,您會注意到工作集大小的增加。 這是因為通用語言運行時提供了許多功能,以確保程式正常運行。 如果 **/clr**應用程式執行不正常,您可能需要啟用 C4793(預設情況下關閉),有關詳細資訊,請參閱[編譯器警告(級別 1 和 3) C4793。](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)

### <a name="program-crashes-on-shutdown"></a>程式在關閉時崩潰

在某些情況下,CLR 可以在託管代碼完成運行之前關閉。 使用`std::set_terminate``SIGTERM`和可能會導致此。 有關詳細資訊[,請參閱信號常量](../c-runtime-library/signal-constants.md)和[set_terminate。](../c-runtime-library/abnormal-termination.md)

## <a name="using-new-visual-c-features"></a>使用新的視覺C++功能

在應用程式編譯、鏈接和運行後,可以在使用 **/clr**編譯的任何模組中使用 .NET 功能。 如需詳細資訊，請參閱[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)。

有關 Visual C++ 中的 .NET 編程的資訊,請參閱:

- [.NET 程式設計,帶C++/CLI(視覺C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

- [本機與 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)

- [執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
