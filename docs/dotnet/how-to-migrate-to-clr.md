---
title: "如何：移轉至 /clr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], 移植至"
  - "編譯機器碼 [C++]"
  - "Interop [C++], /clr 編譯器選項"
  - "互通性 [C++], /clr 編譯器選項"
  - "移轉 [C++], /clr 編譯器選項"
  - "升級 Visual C++ 應用程式, /clr 編譯器選項"
ms.assetid: c9290b8b-436a-4510-8b56-eae51f4a9afc
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：移轉至 /clr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題討論當以 **\/clr** 編譯原生程式碼時所產生的問題 \(如需詳細資訊，請參閱 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md)\)。  **\/clr** 允許 Visual C\+\+ 模組從 .NET 組件叫用 \(Invoke\) 和被叫用，同時還能保持與 Unmanaged 模組的相容性。  如需以 **\/clr** 進行編譯之優點的詳細資訊，請參閱 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)和[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)。  
  
## 以 \/clr 編譯程式庫專案的已知問題  
 使用 **\/clr** 編譯程式庫專案時，Visual Studio 會有一些已知問題：  
  
-   您的程式碼可以在執行階段使用 [CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md) 來查詢型別。  但是，如果型別在 MSIL .dll 中 \(以 **\/clr** 編譯\)，則對 [CRuntimeClass::FromName](../Topic/CRuntimeClass::FromName.md) 的呼叫如果是發生在於 Managed .dll 中執行靜態建構函式之前，則可能會失敗 \(如果 FromName 呼叫發生在於 Managed .dll 中執行程式碼之後，則不會有這個問題\)。  若要避開這個問題，您可以在 Managed .dll 中定義函式、將它匯出，以及從原生 MFC 應用程式叫用它，以強制建構 Managed 靜態建構函式。  例如：  
  
    ```  
    // Extension DLL Header file:  
    __declspec( dllexport ) void EnsureManagedInitialization () {  
       // managed code that won't be optimized away  
       System::GC::KeepAlive(System::Int32::MaxValue);  
    }  
    ```  
  
## 以 Visual C\+\+ 進行編譯  
 在您的專案中的任何模組上使用 **\/clr** 之前，請先以 Visual Studio 2010 編譯和連結您的原生專案。  
  
 下列步驟是依照順序排列，提供了最簡單的 **\/clr** 編譯方法，  執行了下列每一個步驟之後，請務必編譯及執行專案。  
  
### Visual C\+\+ 2003 之前的版本  
 如果您是從 Visual C\+\+ 2003 之前的版本升級至 Visual Studio 2010，則可能會看到與 Visual C\+\+ 2003 中增強之 C\+\+ 標準一致性有關的編譯器錯誤。  
  
### 從 Visual C\+\+ 2003 升級  
 先前以 Visual C\+\+ 2003 建置的專案，也應該要先在不搭配 **\/clr** 的情況下進行編譯，因為 Visual Studio 已經提升了 ANSI\/ISO 相容性，並且包含一些重大變更。  最值得注意的變更可能就是 [CRT 中的安全性功能](../c-runtime-library/security-features-in-the-crt.md)。  使用 CRT 的程式碼很可能會產生反對警告訊息，  您可以隱藏這些警告訊息，但最好是移轉至新的 [CRT 函式的安全性增強版本](../c-runtime-library/security-enhanced-versions-of-crt-functions.md)，因為它們可以提供更好的安全性，並且可以揭露程式碼中的安全性問題。  
  
### 從 Managed Extensions for C\+\+ 升級  
 以 Visual C\+\+ .NET 或 Visual C\+\+ 2003 建置並使用 Managed Extensions for C\+\+ 的專案至少需要變更一項專案設定，因為這些擴充功能現在已經被取代，  因此，以 Managed Extensions for C\+\+ 撰寫的程式碼無法在 **\/clr** 下進行編譯。  請改用 **\/clr:oldSyntax**。  
  
## 將 C 程式碼轉換成 C\+\+  
 雖然 Visual Studio 將會編譯 C 檔案，卻必須將它們轉換成 C \+\+ 以進行 **\/clr** 編譯。  實際的檔案名稱並不需要變更，您可以使用 **\/Tp** \(請參閱 [\/Tc、\/Tp、\/TC、\/TP \(指定原始程式檔類型\)](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)\)。請注意，雖然 C\+\+ 原始程式碼檔案必要於 **\/clr**，卻不需要重構程式碼也能使用物件導向開發架構。  
  
 若要將 C 程式碼編譯成 C\+\+ 檔案，您很可能必須變更 C 程式碼。  C\+\+ 型別安全規則很嚴格，因此必須以轉換 \(Cast\) 明確地進行型別轉換，  例如，malloc 會傳回 Void 指標，但可以使用轉換 \(Cast\) 指派給指標至 C 的任何型別：  
  
```  
int* a = malloc(sizeof(int));   // C code  
int* b = (int*)malloc(sizeof(int));   // C++ equivalent  
```  
  
 在 C\+\+ 中，函式指標也具有嚴格的型別安全，所以下列 C 程式碼必須加以修改。  在 C\+\+ 中，最好是建立會定義函式指標型別的 `typedef`，然後使用該型別來轉換函式指標：  
  
```  
NewFunc1 = GetProcAddress( hLib, "Func1" );   // C code  
typedef int(*MYPROC)(int);   // C++ equivalent  
NewFunc2 = (MYPROC)GetProcAddress( hLib, "Func2" );  
```  
  
 此外，C\+\+ 還要求函式必須是原型或是經過完整定義，才能參考或叫用函式。  
  
 如果 C 程式碼中所用的識別項剛好是 C\+\+ 中的關鍵字 \(例如 `virtual`、`new`、`delete`、`bool`、`true`、`false` 等等\)，就必須加以重新命名，  您通常可以使用簡單的搜尋與取代作業來完成這項工作。  
  
 最後，C\-Style COM 呼叫必須明確地使用 v\-table 和 `this` 指標，但 C\+\+ 並不會：  
  
```  
COMObj1->lpVtbl->Method(COMObj, args);  // C code  
COMObj2->Method(args);  // C++ equivalent  
```  
  
## 重新進行專案設定  
 在編譯您的專案並在 Visual Studio 2010 中執行之後，您應該要建立 **\/clr** 的新專案組態，而非修改預設組態。  **\/clr** 與某些編譯器選項不相容，並會建立個別的組態，可讓您將專案建置為原生或 Managed 專案。  在 \[屬性頁\] 對話方塊中選取了 **\/clr** 時，和 **\/clr** 不相容的專案設定會被停用 \(如果之後取消選取 **\/clr**，停用的選項並不會自動回復成原狀\)。  
  
### 建立新的專案組態  
 您可以使用 [New Project Configuration Dialog Box](http://msdn.microsoft.com/zh-tw/cca616dc-05a6-4fe3-bdc1-40c72a66f2be)中的 \[**複製設定值來源**\] 選項依據現有的專案設定來建立專案組態，  請針對偵錯組態進行一次這項作業，並針對發行組態進行一次，  然後就可以將後續變更套用至特定的 **\/clr** 組態，並保持原來的專案組態不變。  
  
 您可能需要額外留意那些使用自訂建置規則的專案。  
  
 這個步驟對於使用 Makefile 的專案而言具有不同的含意，  在這種情況下，您可以設定分開的建置目標，或者是從原始版本建立 **\/clr** 編譯專用的版本。  
  
### 變更專案設定  
 您可以依照 [\/clr \(Common Language Runtime 編譯\)](../build/reference/clr-common-language-runtime-compilation.md) 中的指示，在開發環境中選取 **\/clr**。  如先前所述，這個步驟會自動停用衝突的專案設定。  
  
> [!NOTE]
>  將 Managed 程式庫或 Web 服務專案從 Visual C\+\+ 2003 升級時，**\/Zl** 編譯器選項會加入至 \[**命令列**\] 屬性頁。  這項動作會造成 LNK2001。  請從 \[**命令列**\] 屬性頁移除 **\/Zl**，以解決問題。  如需詳細資訊，請參閱[\/Zl \(省略預設程式庫名稱\)](../build/reference/zl-omit-default-library-name.md)以及 [如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)。  或者是，將 msvcrt.lib 和 msvcmrt.lib 加入至連結器的 \[**其他相依性**\] 屬性。  
  
 如果是使用 Makefile 建置的專案，一旦加入了 **\/clr**，就必須手動停用不相容的編譯器選項。  如需和 **\/clr** 不相容的編譯器選項的詳細資訊，請參閱 [\/clr 限制](../build/reference/clr-restrictions.md)。  
  
### 先行編譯標頭  
 在 **\/clr** 下，可支援先行編譯的標頭。  不過，如果您只以 **\/clr** 來編譯某些 CPP 檔案 \(以原生方式編譯其餘的 CPP 檔案\)，就必須進行一些變更，因為以 **\/clr** 產生的先行編譯標頭和那些不是以 **\/clr** 產生的先行編譯標頭並不相容。  這種不相容是由 **\/clr** 會產生及需要中繼資料的事實所造成。  因此，以 **\/clr** 編譯的模組不能使用沒有包含中繼資料的先行編譯標頭，而非 **\/clr** 模組則不能使用包含了中繼資料的先行編譯標頭檔。  
  
 如果某個專案中有一些模組是以 **\/clr** 編譯而成，則編譯此專案最簡單的方式就是全部停用先行編譯的標頭 \(在專案的 \[屬性頁\] 對話方塊中，開啟 \[C\/C\+\+\] 節點，然後選取 \[先行編譯標頭\]，  接著將 \[建立\/使用先行編譯標頭\] 屬性變更為 \[未使用先行編譯標頭檔\]\)。  
  
 不過，尤其是大型專案，先行編譯的標頭可提供更快的編譯速度，因此停用這項功能並不是十分妥當。  在這種情況下，最好是將 **\/clr** 與非 **\/clr** 檔案設定成使用分開的先行編譯標頭。  只要一個步驟就能完成這項作業：請使用 \[方案總管\] 選取多個以 **\/clr** 編譯的模組，以滑鼠右鍵按一下此群組，然後選取 \[屬性\]，  接著將 \[透過檔案建立\/使用 PCH\] 與 \[先行編譯標頭檔\] 這兩個屬性變更為分別使用不同的標頭檔名稱與 PCH 檔案。  
  
## 修正錯誤  
 以 **\/clr** 進行編譯可能會造成編譯器、連結器或執行階段錯誤。  這一節將討論最常見的問題。  
  
### 中繼資料合併  
 不同的資料型別版本可能會造成連結器失敗，因為針對兩種型別所產生的中繼資料並不相符 \(當某個型別的成員是以條件方式定義，但使用此型別的所有 CPP 檔案的條件並不相同時，通常會造成這種問題\)。在這種情況下，連結器會失敗，只報告符號名稱以及定義了型別的第二個 OBJ 檔案的名稱。  調換 OBJ 檔案傳送至連結器的順序，以發現資料型別之其他版本的位置，通常會很有用。  
  
### 載入器鎖定死結  
 在 Visual C\+\+ .NET 和 Visual C\+\+ 2003 中，在 **\/clr** 下進行初始設定很容易受到非決定性死結的影響，  這個問題就是已知的「載入器鎖定死結」。  在 Visual Studio 2010 中，比較容易避免發生這個死結，在執行階段就會對它進行偵測並加以報告，而且它也不再具有決定性。  您還是可能會遇到載入器鎖定的問題，但現在比較容易避免及修正這個問題。  如需詳細背景資訊、指導方針與解決方案，請參閱[混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)。  
  
### 資料匯出  
 匯出 DLL 資料很容易發生錯誤，我們不建議這麼做，  這是因為直到已經執行了 DLL 的某些 Managed 部分，才能保證會初始化 DLL 的資料區段。  請參考 [\#using 指示詞](../preprocessor/hash-using-directive-cpp.md)的中繼資料。  
  
### 型別可視性  
 原生型別現在預設是私用型別。  在 Visual C\+\+ .NET 2002 和 Visual C\+\+ 2003 中，原生型別預設是公用型別，  這可能會造成在 DLL 外無法看到原生型別。  請將 `public` 加入至這些型別，以解決這個問題。  如需詳細資訊，請參閱[類型和成員可視性](../misc/type-and-member-visibility.md)。  
  
### 浮點和對齊問題  
 Common Language Runtime 上不支援 `__controlfp` \(如需詳細資訊，請參閱 [\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)\)。  此外，CLR 也不理會 [align](../cpp/align-cpp.md)。  
  
### COM 初始設定  
 當初始化模組時，Common Language Runtime 會自動初始化 COM \(當自動初始化 COM 時，就像是 MTA 一樣\)。  結果，明確地初始化 COM 會產生傳回碼，指出 COM 早已經初始化了。  當 CLR 已經將 COM 初始化為某個執行緒處理模型時，嘗試以另一個執行緒處理模型明確初始化 COM 可能會讓應用程式失敗。  
  
 根據預設，Common Language Runtime 會以 MTA 的方式啟動 COM；請使用 [\/CLRTHREADATTRIBUTE \(設定 CLR 執行緒屬性\)](../build/reference/clrthreadattribute-set-clr-thread-attribute.md) 來修改這個問題。  
  
### 效能問題  
 當間接呼叫產生至 MSIL 的原生 C\+\+ 方法時 \(虛擬函式呼叫或使用函式指標\)，您可能會發現效能降低了。  若要進一步了解這個問題，請參閱 [Double Thunking](../dotnet/double-thunking-cpp.md)。  
  
 從原生移至 MSIL 時，您會發現工作集的大小增加了，  這是因為 Common Language Runtime 會提供許多功能，以確保程式能夠正確執行。  如果 **\/clr** 應用程式沒有正確執行，您可能需要啟用 C4793 \(預設是停用狀態\)。如需詳細資訊，請參閱[編譯器警告 \(層級 1 和 3\) C4793](../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)。  
  
### 關機時程式當掉  
 在某些情況下，CLR 可能會在 Managed 程式碼執行完成之前就先關閉。  使用 `std::set_terminate` 和 `SIGTERM` 可能會造成這個問題。  如需詳細資訊，請參閱[signal 常數](../c-runtime-library/signal-constants.md)以及 [set\_terminate](../Topic/set_terminate%20\(%3Cexception%3E\).md)。  
  
## 使用新的 Visual C\+\+ 功能  
 應用程式在編譯、連結與執行之後，您就可以開始在任何以 **\/clr** 編譯的模組中使用 .NET 功能。  如需詳細資訊，請參閱[Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)。  
  
 如果使用了 Managed Extensions for C\+\+，您可以將程式碼轉換成使用新的語法。  如需語法差異的摘要列表，請參閱 [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/zh-tw/edbded88-7ef3-4757-bd9d-b8f48ac2aada)。  如需轉換 Managed Extensions for C\+\+ 的詳細資訊，請參閱 [C\+\+\/CLI 移轉入門](../dotnet/cpp-cli-migration-primer.md)。  
  
 如需以 Visual C\+\+ 進行 .NET 程式設計的詳細資訊，請參閱：  
  
-   [以 C\+\+\/CLI 進行 .NET 程式設計](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
  
-   [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)  
  
-   [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)