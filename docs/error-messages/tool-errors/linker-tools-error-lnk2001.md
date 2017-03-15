---
title: "連結器工具錯誤 LNK2001 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9dee257bec0f09bd729bf10c4a1468ecb20dfa61
ms.openlocfilehash: 3629075e5659cb89ab751b011f3ce2cbf89397cc
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2001"></a>連結器工具錯誤 LNK2001
無法解析的外部符號 「 符號 」  
  
 程式碼參考的項目 （例如函式、 變數或標籤） 連結器找不到程式庫和物件檔案。  
  
 此錯誤訊息後面是嚴重錯誤[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。  
  
 **可能的原因**  
  
-   從 Visual c + + 2003 中，升級的 managed 程式庫或 web 服務專案時**/Zl**編譯器選項加入至**命令列**屬性頁。 這會造成 LNK2001。  
  
     若要解決此錯誤，請新增 msvcrt.lib 和 msvcmrt.lib 給連結器的其他相依性屬性。 或者，您也可以移除**/Zl**從**命令列**屬性頁。 如需詳細資訊，請參閱[/Zl （省略預設程式庫名稱）](../../build/reference/zl-omit-default-library-name.md)和[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
-   程式碼的要求不存在 （符號拼法不正確，或使用錯誤的情況下，例如）。  
  
-   程式碼要求錯誤 （您正在使用的程式庫，某些版本的產品，其他人從另一個版本的混合的版本） 的項目。  
  
 **特定的原因**  
  
 **程式碼問題**  
  
-   如果 LNK2001 診斷文字報告`__check_commonlanguageruntime_version`是未解析的外部符號，請參閱[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)如何解決問題的資訊。  
  
-   成員樣板的定義是在類別之外。 Visual c + + 有的限制，在其中成員樣板必須完整定義在封閉式類別中。 請參閱知識庫文章 Q239436 LNK2001 和成員範本的相關資訊。  
  
-   不相符的情況下在程式碼或模組定義 (.def) 檔案可能造成 LNK2001。 例如，如果您在名為變數`var1`一個 c + + 原始程式檔，並嘗試將它做為存取`VAR1`在另一個。  
  
-   使用的專案[函式內嵌](../../error-messages/tool-errors/function-inlining-problems.md)尚未定義的函式在.cpp 檔案，而非標頭中的檔案會造成 LNK2001。  
  
-   從 c + + 程式中呼叫 C 函式，而不需使用`extern`"C"（這會導致編譯器使用 C 命名慣例） 會造成 LNK2001。 編譯器選項[/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)和[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)會導致編譯器檔案分別編譯為 c 或 C，而不管副檔名。 這些選項會使不同於您所預期的函式名稱。  
  
-   嘗試參考函式或不具有外部連結的資料會造成 LNK2001。 在 c + + 內嵌函式和`const`資料具有內部連結，除非明確指定為`extern`。  
  
-   A[遺漏函式主體或變數](../../error-messages/tool-errors/missing-function-body-or-variable.md)會造成 LNK2001。 只要函式原型或`extern`宣告，編譯器可以繼續而沒有錯誤，但連結器無法解析的呼叫至地址或變數的參考，因為沒有任何函式程式碼或變數保留的空間。  
  
-   不符合函式宣告中的參數型別來呼叫函式會造成 LNK2001。 [名稱裝飾](../../error-messages/tool-errors/name-decoration.md)函式的參數納入最終的裝飾函式名稱。  
  
-   不正確地包含的原型，使編譯器預期未提供的函式主體會造成 LNK2001。 如果您有的類別和非類別函式實作的`F`，要小心的 c + + 範圍解析規則。  
  
-   在使用 c + + 時，在類別定義包括函式原型，而且未[包含實作](../../error-messages/tool-errors/missing-function-body-or-variable.md)該類別的函式會造成 LNK2001。  
  
-   嘗試從建構函式或解構函式的抽象基底類別呼叫純虛擬函式會造成 LNK2001。 純虛擬函式有沒有基底類別實作。  
  
-   函式中嘗試使用的變數宣告 ([區域變數](../../error-messages/tool-errors/automatic-function-scope-variables.md)) 之外，該函式的範圍會造成 LNK2001。  
  
-   在建置發行版本的 ATL 專案時，表示需要 CRT 啟始程式碼。 若要修正，請執行下列其中一項  
  
    -   移除`_ATL_MIN_CRT`從清單中的前置處理器定義允許包含 CRT 啟始程式碼。 請參閱[一般組態設定的屬性頁](../../ide/general-property-page-project.md)如需詳細資訊。  
  
    -   可能的話，請移除需要 CRT 啟始程式碼的 CRT 函式呼叫。 相反地，Win32 用法。 例如，使用`lstrcmp`而不是`strcmp`。 已知需要 CRT 啟始程式碼的函式是其中一個字串和浮點函式。  
  
 **編譯與連結問題**  
  
-   專案遺漏程式庫的參考 (。LIB) 或物件 (。OBJ) 檔案。 請參閱[.lib 檔做為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)如需詳細資訊。  
  
-   如果您使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)或[/Zl](../../build/reference/zl-omit-default-library-name.md)，程式庫包含必要的程式碼將不會連結到專案除非您明確地加入它們。 (使用編譯時**/clr**或**/clr: pure**，您會看到.cctor 的參考，請參閱[初始化的混合的組件](../../dotnet/initialization-of-mixed-assemblies.md)如需詳細資訊。)  
  
-   如果您使用 Unicode 和 MFC，您將會發生未解析的外部`_WinMain@16`如果您未建立至進入點`wWinMainCRTStartup`; 使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)。 請參閱[Unicode 程式設計摘要](../../text/unicode-programming-summary.md)。  
  
     請參閱下列知識庫文件，位於 MSDN Library，如需詳細資訊。 在 MSDN Library 中，按一下 [**搜尋**] 索引標籤上，將文件編號或文件標題貼到文字方塊中，然後按一下**列出主題**。 如果您搜尋文件編號，請確定**搜尋僅標題**選項已清除。  
  
    -   Q125750"PRB︰ 錯誤 LNK2001: '_WinMain@16': 無法解析的外部符號 」  
  
    -   Q131204"PRB︰ 錯誤的專案選取範圍會造成 LNK2001 _WinMain@16」  
  
    -   Q100639 「 Unicode 支援 Microsoft foundation 類別的程式庫 」  
  
    -   Q291952"PRB︰ 連結錯誤 LNK2001︰ 無法解析的外部符號 _main 」  
  
-   連結程式庫 LIBC.lib 以 /MT 編譯程式碼會造成 LNK2001 `_beginthread`， `_beginthreadex`， `_endthread`，和`_endthreadex`。  
  
-   連結需要多執行緒程式庫的程式碼 (任何 MFC 程式碼或以編譯程式碼[/MT](../../build/reference/md-mt-ld-use-run-time-library.md)) 會造成 LNK2001 [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md)， `_beginthreadex`， [_endthread](../../c-runtime-library/reference/endthread-endthreadex.md)，和`_endthreadex`。 請參閱下列知識庫文件，如需詳細資訊︰  
  
    -   Q126646"PRB︰ 錯誤訊息︰ LNK2001 上 __beginthreadex 和\__endthreadex 」  
  
    -   Q128641 」 資訊︰ /Mx 編譯器選項和 LIBC、 LIBCMT、 MSVCRT 程式庫 」  
  
    -   Q166504"PRB: MFC 和 CRT 必須符合在偵錯/發行和靜態/動態 」  
  
-   進行編譯時**/MD**，「 func 」 來源中的參考會變成參考 「`__imp__func`」 物件，因為所有執行階段現在會都保留在 DLL 中。 如果您嘗試使用靜態程式庫 LIBC.lib 或 LIBCMT.lib 連結時，您將會發生 LNK2001 `__imp__func`。 如果您嘗試連結 MSVCxx.lib /MD 不進行編譯時就不一定會 LNK2001，但您可能會發生其他問題。  
  
-   連結與發行模式程式庫建置應用程式的偵錯版本時，會造成 LNK2001。 同樣地，使用**/Mxd**選項 (**/MTd**，或**/MDd**) 和 （或) 定義`_DEBUG`，接著再連結發行程式庫會提供您可能無法解析的外部符號 （還有其他問題）。 連結偵錯程式庫建置的發行模型也會造成類似的問題。  
  
-   Microsoft 程式庫及編譯器產品的混合版本可能會造成問題。 新編譯器版本的程式庫可能包含新與舊版程式庫中找不到的符號。 若要變更目錄中的搜尋路徑，或變更它們的順序來指向目前的版本。  
  
     [工具 |選項 |專案 |VC + + 目錄] 對話方塊中的，在程式庫檔案選取範圍，可讓您變更搜尋順序。 在專案屬性頁對話方塊中的連結器資料夾也可能包含可能是過期的路徑。  
  
     （例如傳送至不同的位置），安裝新的 SDK 和搜尋順序不會更新為指向新位置時，可能會出現此問題。 一般來說，您應該將路徑放至新的 Sdk 包含和 lib 預設 Visual c + + 位置前面的目錄。 此外，含有內嵌的路徑的專案可能仍然指向舊的路徑有效，但過期會安裝到不同位置的新版本所加入的新功能。  
  
-   目前沒有任何標準[c + + 命名](../../error-messages/tool-errors/name-decoration.md)編譯器廠商或不同的編譯器版本之間。 因此，連結以其他編譯器編譯的目的檔不可能會產生相同的命名配置，因而造成 LNK2001 錯誤。  
  
-   [混合內嵌與非內嵌編譯選項](../../error-messages/tool-errors/function-inlining-problems.md)在不同模組會造成 LNK2001。 如果 c + + 程式庫會建立函式內嵌開啟 (**/Ob1**或**/Ob2**)，但描述該函式對應的標頭檔已關閉內嵌 (沒有`inline`關鍵字)，就會發生此錯誤。 若要避免這個問題，已經內嵌函式定義與`inline`中要包含在其他檔案的標頭檔。  
  
-   如果您使用`#pragma inline_depth`編譯器指示詞，請確定您有[值 2 或更大的集](../../error-messages/tool-errors/function-inlining-problems.md)，並確定您使用[/Ob1](../../build/reference/ob-inline-function-expansion.md)或[/Ob2](../../build/reference/ob-inline-function-expansion.md)編譯器選項。  
  
-   省略 LINK 選項 /NOENTRY 建立僅含資源的 DLL 時就會造成 LNK2001。  
  
-   使用不正確的 /SUBSYSTEM 或 /ENTRY 設定可能造成 LNK2001。 例如，如果您撰寫字元為基礎的應用程式 （主控台應用程式），並指定 /SUBSYSTEM:WINDOWS，就會無法解析的外部`WinMain`。 如需有關這些選項和進入點的詳細資訊，請參閱[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)和[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項。  
  
 **匯出問題**  
  
-   當您將移植從 16 到 32 或 64 位元的應用程式時，可能會發生 LNK2001。 目前的模組定義 (.def) 檔語法需要`__cdecl`， `__stdcall`，和`__fastcall`EXPORTS 區段會列出函式沒有底線 （裝飾）。 這與 16 位元語法，其中必須列出以底線 （裝飾） 不同。 如需詳細資訊，請參閱的描述[匯出](../../build/reference/exports.md)模組定義檔的區段。  
  
-   .Def 檔案中列出，但找不到任何匯出將會造成 LNK2001。 這可能是因為它不存在、 拼法不正確，或使用 c + + 裝飾的名稱 （.def 檔不接受裝飾的名稱）  
  
 **解譯輸出**  
  
 無法解析的符號時，您可以取得函數的相關資訊由下列指導方針︰  
  
 在 x86 平台，呼叫慣例裝飾名稱編譯在 C 中，或 extern"C"c + + 中的名稱是︰  
  
 `__cdecl`  
 函式具有底線 (_) 的前置詞。  
  
 `__stdcall`  
 函式具有底線 (_) 的前置詞和後置字元，後面接著 dword @ 對齊參數在堆疊上的大小。  
  
 `__fastcall`  
 函式具有 @ 前置詞和後置字元，後面接著 dword @ 對齊參數在堆疊上的大小。  
  
 您可以使用 undname.exe 取得裝飾名稱的未裝飾的形式。  
  
 如需上述原因的詳細資訊，請參閱[名稱裝飾](../../error-messages/tool-errors/name-decoration.md)。
