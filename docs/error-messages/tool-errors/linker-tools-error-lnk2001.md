---
title: "連結器工具錯誤 LNK2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2001"
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# 連結器工具錯誤 LNK2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法解析的外部符號 "symbol"  
  
 程式碼參考到連結器在程式庫與目的檔中找不到的項目 \(例如函式、變數或標籤\)。  
  
 這個錯誤訊息之後會出現嚴重錯誤 [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。  
  
 **可能的原因**  
  
-   將 Managed 程式庫或 Web 服務專案從 Visual C\+\+ 2003 升級時，**\/Zl** 編譯器選項會加入至 \[**命令列**\] 屬性頁。  這項動作會造成 LNK2001。  
  
     若要解決這個錯誤，請將 msvcrt.lib 和 msvcmrt.lib 加入至連結器的 \[其他相依性\] 屬性。  或者，從 \[**命令列**\] 屬性頁移除 **\/Zl**。  如需詳細資訊，請參閱[\/Zl \(省略預設程式庫名稱\)](../../build/reference/zl-omit-default-library-name.md)與[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
-   程式碼要求的項目不存在 \(例如符號拼錯，或大小寫使用不正確\)。  
  
-   程式碼要求了錯誤的項目 \(您正在使用一個混合版本的程式庫，其中有些來自該產品的某一版本，有些則來自其他版本\)。  
  
 **明確原因**  
  
 **程式碼問題**  
  
-   如果 LNK2001 診斷內容中報告 `__check_commonlanguageruntime_version` 為無法解析的外部符號，請參閱 [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)，取得如何解決此問題的詳細資訊。  
  
-   成員樣板定義沒有在這個類別中。  Visual C\+\+ 限制成員樣板必須完全定義於封入類別 \(Enclosing Class\) 之內。  如需 LNK2001 和成員樣板的詳細資訊，請參閱知識庫 \(Knowledge Base\) 文件 Q239436。  
  
-   程式碼或模組定義檔 \(Module\-Definition File，.def\) 的大小寫若不相符，就會造成 LNK2001。  例如，如果您在 C\+\+ 的一個原始程式檔 \(Source File\) 中將變數命名為 `var1`，而嘗試在其他原始程式檔中以 `VAR1` 存取該變數，就會出現這個錯誤。  
  
-   使用[函式內嵌](../../error-messages/tool-errors/function-inlining-problems.md) \(Inline\) 的專案，卻在 .cpp 檔而不是標頭檔 \(Header File\) 中定義該函式，就可能會造成 LNK2001。  
  
-   不使用 `extern` "C" \(這可以讓編譯器使用 C 的命名慣例\) 來從 C\+\+ 程式呼叫 C 函式會造成 LNK2001。  編譯器選項 [\/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 和 [\/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 會使編譯器將檔案分別編譯為 C 或 C\+\+，而不管副檔名是什麼。  這些選項會使函式名稱不同於您所預期的名稱。  
  
-   嘗試參考沒有外部連結 \(External Linkage\) 的函式或資料會造成 LNK2001。  在 C\+\+ 中，除非明確指定為 `extern`，否則內嵌函式與 `const` 資料都有內部連結 \(Internal Linkage\)。  
  
-   [遺漏函式主體或變數](../../error-messages/tool-errors/missing-function-body-or-variable.md)會造成 LNK2001。  只要有了函式原型 \(Prototype\) 或 `extern` 宣告，編譯器就可以在沒有錯誤情況下繼續執行，但連結器將無法解析對位址的呼叫或對變數的參考，因為沒有預留的函式碼或變數空間。  
  
-   用不符合函式宣告的參數型態呼叫函式會造成 LNK2001。  [名稱裝飾](../../error-messages/tool-errors/name-decoration.md) \(Name Decoration\) 會將函式的參數合併至最後的裝飾函式名稱。  
  
-   加入了不正確的原型，使編譯器預期函式主體但該主體卻不存在就會造成 LNK2001。  如果您同時以類別與非類別來實作函式 `F`，請注意 C\+\+ 的範圍解析 \(Scope\-Resolution\) 規則。  
  
-   使用 C\+\+ 時，若將函式原型包含在類別定義中而沒有對該類別函式[加入實作](../../error-messages/tool-errors/missing-function-body-or-variable.md)就會造成 LNK2001。  
  
-   嘗試由抽象基底類別的建構函式 \(Constructor\) 或解構函式 \(Destructor\) 呼叫純虛擬函式 \(Pure Virtual Function\) 就會造成 LNK2001。  純虛擬函式沒有基底類別 \(Base Class\) 實作。  
  
-   嘗試在函式範圍之外使用宣告於函式之內的變數 \([區域變數](../../error-messages/tool-errors/automatic-function-scope-variables.md)\) 會造成 LNK2001。  
  
-   建置 ATL 專案的發行版本 \(Release Version\) 就是表示需要該 CRT 啟始程式碼 \(Startup Code\)。  若要修復，請進行下列步驟之一：  
  
    -   自前置處理器 \(Preprocessor\) 定義清單移除 `_ATL_MIN_CRT`，以允許包含 CRT 啟始程式碼。  如需詳細資訊，請參閱[一般組態設定屬性頁](../../ide/general-property-page-project.md)。  
  
    -   如果可能的話，請移除需要 CRT 啟始程式碼的 CRT 函式呼叫。  並取而以相同的 Win32 用法代之。  例如，使用 `lstrcmp` 而非 `strcmp`。  目前已知會需要 CRT 啟始程式碼的函式是某些字串函式與浮點函式。  
  
 **編譯與連結問題**  
  
-   這個專案遺漏程式庫 \(.LIB\) 或物件 \(.OBJ\) 檔的參考。  如需詳細資訊，請參閱 [.lib 檔案當成連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。  
  
-   如果您使用 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) 或 [\/Zl](../../build/reference/zl-omit-default-library-name.md)，那麼除非您已明確地將程式碼包含在內，否則包含必要程式碼的程式庫將無法連結到專案之中 \(以 **\/clr** 或 **\/clr:pure** 編譯時，您會看到 .cctor 的參考：如需詳細資訊，請參閱[混合組件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)\)。  
  
-   如果您使用的是 Unicode 和 MFC，而且未建立 `wWinMainCRTStartup` 的進入點，就會在 `_WinMain@16` 上發生無法解析的外部錯誤；請使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md)。  請參閱 [Unicode 程式設計摘要](../../text/unicode-programming-summary.md)。  
  
     如需詳細資訊，請參閱下列位於 MSDN Library 中的知識庫文件。  請在 MSDN Library 中按一下 \[**搜尋**\] 索引標籤，將文件編號或文件標題貼在文字方塊中，接著再按一下 \[**列出主題**\]。  如果您是以文件編號搜尋，請確定已清除 \[**只搜尋標題**\] 選項。  
  
    -   Q125750   "PRB: Error LNK2001: '\_WinMain@16': Unresolved External Symbol"  
  
    -   Q131204   "PRB: Wrong Project Selection Causes LNK2001 on \_WinMain@16"  
  
    -   Q100639   "Unicode Support in the Microsoft Foundation Class Library"  
  
    -   Q291952    "PRB: Link Error LNK2001: Unresolved External Symbol \_main"  
  
-   連結使用 \/MT 編譯的程式碼和 LIBC.lib 程式庫，會造成 `_beginthread`、`_beginthreadex`、`_endthread` 和 `_endthreadex` 的 LNK2001。  
  
-   連結需要多執行緒程式庫 \(任何 MFC 程式碼或以 [\/MT](../../build/reference/md-mt-ld-use-run-time-library.md) 編譯的程式碼\) 的程式碼，會造成 [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)、`_beginthreadex`、[\_endthread](../../c-runtime-library/reference/endthread-endthreadex.md) 和 `_endthreadex` 的 LNK2001。  如需詳細資訊，請參閱下列知識庫文件：  
  
    -   Q126646 "PRB: Error Msg: LNK2001 on \_\_beginthreadex and \_\_endthreadex"  
  
    -   Q128641 "INFO: \/Mx Compiler Options and the LIBC, LIBCMT, MSVCRT Libs"  
  
    -   Q166504 "PRB: MFC and CRT Must Match in debug\/release and static\/dynamic"  
  
-   當您以 **\/MD** 編譯時，原始檔中的 "func" 參考會變成目的檔中的 "`__imp__func`" 參考，因為現在所有的執行階段都會存放在 DLL 之中。  如果您嘗試連結靜態程式庫 LIBC.lib 或 LIBCMT.lib，就會在 `__imp__func` 上造成 LNK2001 錯誤。  如果您嘗試在編譯時未使用 \/MD 連結 MSVCxx.lib，您不一定會造成 LNK2001，但是可能會發生其他問題。  
  
-   在建置偵錯版本的應用程式時，連結發行模式的程式庫會造成 LNK2001。  同樣地，使用 **\/Mxd** 選項 \(**\/MTd** 或**\/MDd**\) 和 \(或\) 定義 `_DEBUG`，然後與發行的程式庫連結，可能會導致無法解析的外部符號及其他問題。  連結以偵錯程式庫建置的發行模型也會產生類似的問題。  
  
-   混合 Microsoft 程式庫和編譯器版本的產品可能會有問題。  新編譯器版本的程式庫可能包含舊版程式庫中找不到的新符號。  您可能會希望變更搜尋路徑中的目錄順序，或變更它們以指向目前版本。  
  
     程式庫檔案選項下的 \[VC\+\+ 目錄\] 對話方塊、專案、選項、工具，可讓您更改搜尋順序。  專案 \[屬性頁\] 對話方塊中的 \[連結器\] 資料夾也可能包含過期的路徑。  
  
     這個問題可能發生在您安裝新版 SDK \(可能安裝至不同的位置\) 時，而搜尋順序尚未更新以指向新的安裝位置時。  在正常情況下，您應該將新 SDK 的 Include 和 Lib 目錄路徑放置在預設的 Visual C\+\+ 位置之前。  此外，含有內嵌路徑的專案可能仍然指向有效的舊路徑，但此路徑對安裝在不同位置的新版本所新增的功能而言已經過期。  
  
-   目前編譯器廠商或不同編譯器版本之間並沒有 [C\+\+ 命名](../../error-messages/tool-errors/name-decoration.md)標準。  因此，連結其他編譯器所編譯的目的檔可能不會產生相同的命名配置，因而造成 LNK2001 錯誤。  
  
-   在不同模組[混合內嵌和非內嵌編譯器選項](../../error-messages/tool-errors/function-inlining-problems.md)，會造成 LNK2001。  如果 C\+\+ 程式庫是在函式內嵌開啟時 \(**\/Ob1** 或 **\/Ob2**\) 建立，但描述該函式之對應標頭檔的內嵌卻是關閉的 \(亦即，沒有 `inline` 關鍵字\)，就會發生這種錯誤。  若要避免這個問題，請在您要包含在其他檔案的標頭檔中，以 `inline` 定義該內嵌函式。  
  
-   如果您正在使用 `#pragma inline_depth` 編譯器指示詞，請確定您的設定值是 [2 或更大值](../../error-messages/tool-errors/function-inlining-problems.md)，並確定您使用的是 [\/Ob1](../../build/reference/ob-inline-function-expansion.md) 或 [\/Ob2](../../build/reference/ob-inline-function-expansion.md) 編譯器選項。  
  
-   建立資源專用 \(Resource\-Only\) 的 DLL 時若省略 LINK 選項 \/NOENTRY，會造成 LNK2001。  
  
-   使用不正確的 \/SUBSYSTEM 或 \/ENTRY 設定，會造成 LNK2001。  例如，如果您在編寫一個以字元為基礎的應用程式 \(主控台應用程式，Console Application\) 時，又指定 \/SUBSYSTEM:WINDOWS，`WinMain` 就會發生無法解析的外部符號。  如需這些選項和進入點 \(Entry Point\) 的詳細資訊，請參閱 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 和 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 連結器選項。  
  
 **匯出問題**  
  
-   當您將應用程式由 16 位元移植為 32 位元或 64 位元時，可能會發生 LNK2001。  目前的模組定義 \(.def\) 檔語法必須要將 `__cdecl`、`__stdcall` 和 `__fastcall` 函式去掉底線 \(未裝飾\)，列於 EXPORTS 區段中。  這麼做有別於 16 位元語法中必須列出底線 \(裝飾\) 的規定。  如需詳細資訊，請參閱模組定義檔中的 [EXPORTS](../../build/reference/exports.md) 章節說明。  
  
-   任何列在 .def 檔且找不到的匯出都會造成 LNK2001。  這可能是因為該匯出並不存在、拼法錯誤或使用了 C\+\+ 的裝飾名稱 \(.def 檔不接受裝飾名稱\)。  
  
 **解譯輸出**  
  
 無法解析符號時，您可以在下列方針中找到該函式的相關資訊：  
  
 在 x86 平台，以 C 編譯的名稱、或以 C\+\+ 編譯的 extern "C" 名稱之呼叫慣例裝飾是：  
  
 `__cdecl`  
 以底線 \(\_\) 開始的函式。  
  
 `__stdcall`  
 以底線 \(\_\) 開始，並以 @ 結尾的函式，後面接著堆疊的參數之 dword 對齊大小。  
  
 `__fastcall`  
 以 @ 開始、@ 結尾的函式，後面接著堆疊的參數之 dword 對齊大小。  
  
 使用 undname.exe 取得裝飾名稱的未裝飾形式。  
  
 如需上述所列原因的詳細資訊，請參閱[名稱裝飾](../../error-messages/tool-errors/name-decoration.md)。