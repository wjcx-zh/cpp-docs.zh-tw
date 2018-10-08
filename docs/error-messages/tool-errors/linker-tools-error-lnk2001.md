---
title: 連結器工具錯誤 LNK2001 |Microsoft Docs
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2001
dev_langs:
- C++
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3da81f46514fbdd7d01ce9c2a9d8be6007301b45
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861573"
---
# <a name="linker-tools-error-lnk2001"></a>連結器工具錯誤 LNK2001

無法解析的外部符號 」*符號*"

已編譯的程式碼會參考或呼叫*符號*，但該符號未定義的任何程式庫或連結器指定的物件檔案。

此錯誤訊息後面接著嚴重錯誤[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)。 您必須修正所有 LNK2001 和 LNK2019 錯誤，若要修正錯誤 LNK1120。

## <a name="possible-causes"></a>可能的原因

有許多方法可取得這項錯誤，但所有人都牽涉到的函式或變數，連結器無法參考*解決*，或尋找的定義。 符號不是時，編譯器能夠識別*宣告*，但不是在未*定義*，因為定義可能是不同的原始程式檔或程式庫中。 如果符號為參考，但永遠不會定義，連結器會產生錯誤。

### <a name="coding-issues"></a>程式碼的問題

此錯誤可能因不相符的情況下，在您的原始碼或模組定義 (.def) 檔案。 例如，如果您為變數命名`var1`一個 c + + 原始程式檔，然後再次嘗試存取為`VAR1`位於另一個，就會產生這個錯誤。 若要修正此問題，使用一致的方式拼字和大小寫名稱。

此錯誤可能造成中使用的專案[函式內嵌](../../error-messages/tool-errors/function-inlining-problems.md)如果您在原始程式檔，而不是在標頭檔中定義的函式。 外部定義它們的原始程式檔，看不到內嵌函式。 若要修正此問題，請在 宣告它們的標頭中定義內嵌函式。

如果您從 c + + 程式呼叫 C 函式不使用，可能會造成這個錯誤`extern "C"`C 函式宣告。 編譯器會使用不同的內部符號命名慣例，C 和 c + + 的程式碼，而且是內部的符號名稱解析的符號時，連結器尋找。 若要修正此問題，請使用`extern "C"`包裝函式用於您的 c + + 程式碼，這會導致編譯器使用這些符號的 C 內部命名慣例的 C 函式的所有宣告。 編譯器選項[/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)並[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)會造成編譯器將檔案編譯成 c + + 或 C，分別，無論檔案副檔名。 這些選項可能會導致不同於您所預期的內部函式名稱。

此錯誤可能被因嘗試參考函式或不具有外部連結的資料。 C + + 內嵌函式和`const`的資料具有內部連結，除非明確指定為`extern`。 若要修正此問題，請使用 明確`extern`上符號的宣告參考外部定義的原始程式檔。

此錯誤可能因[遺漏函式主體或變數](../../error-messages/tool-errors/missing-function-body-or-variable.md)定義。 當您宣告，但未定義，變數、 函式或類別在您的程式碼時，常會使用此錯誤。 編譯器只需要函式原型或`extern`變數的宣告，以產生物件檔案沒有錯誤，但連結器無法解析呼叫函式或變數的參考，因為沒有函式程式碼或變數空間保留。 若要修正此問題，請確定每個參考的函式和變數完全定義在原始程式檔或程式庫包含在您的連結。

此錯誤可能因使用傳回類型與參數類型或不符合函式定義中的呼叫慣例的函式呼叫。 在 c + + 物件檔案中，[名稱裝飾](../../error-messages/tool-errors/name-decoration.md)納入最終的裝飾函式名稱，這用來當做符號來比對時所呼叫的呼叫慣例、 類別或命名空間範圍和傳回類型與參數類型的函式從其他物件檔案的函式會解析。 若要修正此問題，請確定宣告、 定義和所有函式呼叫使用相同範圍、 類型和呼叫慣例。

此錯誤可能造成 c + + 程式碼中，當您在類別定義包括函式原型，但無法[包含實作](../../error-messages/tool-errors/missing-function-body-or-variable.md)函式，然後呼叫它。 若要修正此問題，請務必提供所有呼叫宣告的類別成員的定義。

此錯誤可能被因嘗試從抽象的基底類別呼叫純虛擬函式。 純虛擬函式有沒有基底類別實作。 若要修正此問題，請確定會實作所有呼叫虛擬函式。

此錯誤可能因嘗試使用在函式內宣告的變數 ([區域變數](../../error-messages/tool-errors/automatic-function-scope-variables.md)) 在該函式範圍之外。 若要修正此問題，移除不在範圍內，該變數的參考，或將變數移至較高的範圍。

當您建置發行版本的 ATL 專案，產生 CRT 啟始程式碼是必要的訊息時，會發生此錯誤。 若要修正此問題，請執行下列命令，其中一項

- 移除`_ATL_MIN_CRT`從清單中的前置處理器定義以允許要包含的 CRT 啟始程式碼。 請參閱[一般屬性頁 （專案）](../../ide/general-property-page-project.md)如需詳細資訊。

- 可能的話，請移除對需要 CRT 啟始程式碼的 CRT 函式的呼叫。 請改用 Win32 的對應項。 例如，使用`lstrcmp`而不是`strcmp`。 已知的函式需要 CRT 啟始程式碼是一些字串和浮點函式。

### <a name="compilation-and-link-issues"></a>編譯和連結的問題

專案遺漏的參考文件庫時，會發生此錯誤 (。LIB) 或物件 (。OBJ) 檔案。 若要修正此問題，請先專案中加入必要的程式庫或物件檔案的參考。 如需詳細資訊，請參閱 < [.lib 檔作為連結器輸入](../../build/reference/dot-lib-files-as-linker-input.md)。

如果您使用，可能會發生此錯誤[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)或是[/Zl](../../build/reference/zl-omit-default-library-name.md)選項。 當您指定這些選項時，包含所需的程式碼的程式庫不會連結至專案除非您明確地包含它們。 若要修正此問題，明確地包含您在連結命令列使用的所有程式庫。 如果您使用這些選項時，您會看到許多遺漏 CRT 或標準程式庫函式名稱，明確連結中包含的 CRT 和標準程式庫 Dll 或程式庫檔案。

如果您使用編譯 **/clr**選項，可以有.cctor 遺漏的參考。 若要修正此問題，請參閱[初始化混合組件](../../dotnet/initialization-of-mixed-assemblies.md)如需詳細資訊。

如果您連結至發行模式程式庫建置應用程式的偵錯版本時，會發生此錯誤。 同樣地，如果您使用選項 **/MTd**或是 **/MDd** ，或是定義`_DEBUG`然後連結至發行程式庫，您應該預期許多可能無法解析外部符號，在其他問題。 連結偵錯程式庫的發行模式建置時，也會造成類似問題。 若要修正此問題，請確定您在偵錯組建中，使用偵錯程式庫，並在您的零售的零售版程式庫建置。

如果您的程式碼從一個版本的程式庫，是指一個符號，但是您提供不同版本的連結器程式庫，就會發生此錯誤。 一般而言，您不能混合物件檔案或針對不同版本的編譯器內建的程式庫。 新版本中隨附的程式庫可能包含找不到包含在舊版中，與反向的程式庫中的符號。 若要修正此問題，請建置的所有物件檔案和程式庫與編譯器相同版本之前將它們連結在一起。

- 工具&#124;選項&#124;專案&#124;VC + + 目錄 對話方塊中的，在程式庫檔案選取範圍，可讓您變更程式庫搜尋順序。 在專案的 [屬性頁] 對話方塊中的 [連結器] 資料夾也可能包含可能是過期的路徑。

- 新的 SDK 已安裝 （或許是為了不同的位置），並搜尋順序不會更新以指向新位置時，可能會出現此問題。 一般來說，您應該將新的 SDK 放路徑包含和 lib 目錄前面的預設 Visual c + + 的位置。 此外，專案包含內嵌的路徑可能仍然指向舊的路徑有效，但過時針對至不同的位置安裝新版本所加入的新功能。

- 如果您在命令列建置，並已建立您自己的環境變數，請確認工具、 程式庫和標頭檔的路徑，請移至一致的版本。 如需詳細資訊，請參閱[設定命令列建置的路徑和環境變數](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

目前沒有任何標準[c + + 命名](../../error-messages/tool-errors/name-decoration.md)編譯器廠商或不同的編譯器版本之間。 因此，連結以其他編譯器編譯的目的檔不可能會產生相同的命名配置，因而造成 LNK2001 錯誤。

[混用內嵌和非內嵌編譯選項](../../error-messages/tool-errors/function-inlining-problems.md)上不同的模組可能會造成 LNK2001。 C + + 程式庫會透過函式內嵌開啟 (**/Ob1**或 **/ob2**)，但對應的標頭檔描述該函式已內嵌已關閉 (沒有`inline`關鍵字)，此錯誤就會發生。 若要修正此問題，定義的函式`inline`您在其他原始程式檔中包含的標頭檔。

如果您使用`#pragma inline_depth`編譯器指示詞，請確定您有[值為 2 或更新版本的組](../../error-messages/tool-errors/function-inlining-problems.md)，並確定您也使用[/Ob1](../../build/reference/ob-inline-function-expansion.md)或是[/ob2](../../build/reference/ob-inline-function-expansion.md)編譯器選項。

如果您省略此連結，會發生此錯誤選項 /NOENTRY，當您建立僅含資源的 DLL。 若要修正此問題，請將 /NOENTRY 選項加入連結命令。

如果您使用不正確的 /SUBSYSTEM 或 /ENTRY 設定您的專案中，會發生此錯誤。 例如，如果您撰寫的主控台應用程式，並指定 /subsystem: windows，無法解析的外部錯誤就會產生如`WinMain`。 若要修正此問題，請確定您符合專案類型的選項。 如需有關這些選項和進入點的詳細資訊，請參閱 < [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)並[/ENTRY](../../build/reference/entry-entry-point-symbol.md)連結器選項。

### <a name="exported-symbol-issues"></a>匯出的符號問題

找不到.def 檔案中所列的匯出時，就會發生此錯誤。 這可能是因為它不存在、 拼字不正確，或使用 c + + 裝飾名稱。 .Def 檔不會裝飾的名稱。 若要修正此問題，請移除不必要的匯出，並使用`extern "C"`宣告匯出的符號。

## <a name="what-is-an-unresolved-external-symbol"></a>什麼是未解析的外部符號？

A*符號*是函式或全域變數供內部使用的已編譯的目的檔或程式庫的名稱。 符號是由*定義*物件檔案的全域變數，或函式會配置儲存體的位置放置已編譯的程式碼，函式主體中。 *的外部符號*是一種符號這*參考*，也就是使用或呼叫在某個物件檔中，但在不同的文件庫或物件檔中定義。 *匯出符號*是公開可用所做的目的檔或程式庫中定義的其中一個。 連結器必須*解決*，或找到的相符定義，每個連結到應用程式或 DLL 時，物件檔案所參考的外部符號。 無法在任何連結的檔案中尋找相符的匯出的符號解析的外部符號時，連結器會產生錯誤。

## <a name="use-the-decorated-name-to-find-the-error"></a>使用裝飾的名稱，以找出錯誤

使用的 c + + 編譯器和連結器[名稱裝飾](../../error-messages/tool-errors/name-decoration.md)也稱為*名稱修飾*，用來編碼變數的類型或傳回型別、 參數類型、 範圍和呼叫的額外資訊符號名稱在函式的慣例。 此裝飾的名稱是連結器搜尋來解析外部符號的符號名稱。

因為額外的資訊會成為符號名稱的一部分，如果函式或變數的宣告不完全符合的函式或變數的定義，就可能會造成連接錯誤。 即使在相同的標頭檔會在呼叫程式碼和定義的程式碼中，如果編譯原始程式檔時，會使用不同的編譯器旗標，也可能會發生。 比方說，收到此錯誤，如果您的程式碼會編譯成使用`__vectorcall`呼叫慣例，但您需要呼叫它使用預設的用戶端程式庫的連結`__cdecl`或`__fastcall`呼叫慣例。 在此情況下，符號不相符因為不同的呼叫慣例

為了協助您找出這種錯誤的原因，連結器錯誤訊息顯示這兩個 「 易記名稱，"原始程式碼和未解析的外部符號的裝飾的名稱 （括弧中） 中使用的名稱。 您不需要知道如何轉譯裝飾的名稱，若要能夠與其他的裝飾名稱進行比較。 您可以使用命令列工具，隨附於編譯器來比較預期的符號名稱和實際的符號名稱：

- [/Exports](../../build/reference/dash-exports.md)並[/ 符號](../../build/reference/symbols.md)DUMPBIN 命令列工具選項可協助您探索哪些符號定義在.dll 和物件或程式庫檔案中。 您可以使用此驗證匯出裝飾名稱相符連結器搜尋。

在某些情況下，連結器只會報告的符號的裝飾的名稱。 您可以使用 UNDNAME 命令列工具，以取得裝飾名稱的未裝飾的形式。

## <a name="additional-resources"></a>其他資源

如需 LNK2001 可能原因和解決方案的詳細資訊，請參閱 Stack Overflow 的問題[什麼是未定義參考/未解析的外部符號錯誤以及如何修正它？](http://stackoverflow.com/q/12573816/2002113)。

