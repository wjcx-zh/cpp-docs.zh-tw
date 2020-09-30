---
title: 連結器工具錯誤 LNK1104
description: 描述 Microsoft C 和 c + + (MSVC) 連結器錯誤 LNK1104、其原因和可能的解決方案。
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: aa7bcf34cddfa24956d807131b3c484e7d580e73
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506038"
---
# <a name="linker-tools-error-lnk1104"></a>連結器工具錯誤 LNK1104

> 無法開啟檔案 '*filename*'

當連結器無法開啟檔案（可供讀取或寫入）時，就會回報此錯誤。 問題的兩個最常見原因包括：

- 您的程式已經在執行中，或已載入偵錯工具中，

- 您的程式庫路徑不正確，或不是以雙引號括住。

此錯誤有許多其他可能的原因。 若要縮小這些範圍，請先檢查何種檔案 *檔案名* 。 然後，請使用下列各節來協助找出並修正特定問題。

## <a name="cant-open-your-app-or-its-pdb-file"></a>無法開啟您的應用程式或其 .pdb 檔案

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>您的應用程式正在執行，或已在偵錯工具中載入

當 *filename* 是您的可執行檔名稱或相關聯的 .pdb 檔案時，請查看您的應用程式是否已在執行中。 然後檢查是否已在偵錯工具中載入。 若要修正此問題，請先停止程式並從偵錯工具卸載，再重新建立。 如果應用程式是在另一個程式（例如資源編輯器）中開啟，請將它關閉。 如果您的程式沒有回應，您可能需要使用工作管理員來結束進程。 您可能也需要關閉並重新啟動 Visual Studio。

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>您的應用程式已透過防毒軟體掃描鎖定

防毒程式通常會暫時封鎖對新建立之檔案的存取，特別是 .exe 和 .dll 可執行檔。 若要修正此問題，請嘗試從防毒軟體掃描器排除您的專案組建目錄。

## <a name="cant-open-a-microsoft-library-file"></a>無法開啟 Microsoft 程式庫檔案

### <a name="windows-libraries-such-as-kernel32lib"></a>Windows 程式庫，例如 kernel32.dll .lib

如果無法開啟的檔案是 Microsoft 所提供的其中一個標準程式庫檔案，例如 *kernel32.dll*，您可能會發生專案設定錯誤或安裝錯誤。 確認已安裝 Windows SDK。 如果您的專案需要其他 Microsoft 程式庫（例如 MFC），請確定 MFC 元件也是由 Visual Studio 安裝程式所安裝。 您可以重新執行安裝程式，以在任何時間新增選用的元件。 如需詳細資訊，請參閱 [修改 Visual Studio](/visualstudio/install/modify-visual-studio)。 您可以使用安裝程式中的 [ **個別元件** ] 索引標籤，選擇特定的程式庫和 sdk。

### <a name="versioned-vcruntime-libraries"></a>已建立版本的 vcruntime 程式庫

如果錯誤訊息具有版本設定的 Microsoft 程式庫（例如 *msvcr120.dll*），則可能不會安裝該編譯器版本的平臺工具組。 若要修正此問題，您有兩個選項：升級專案以使用目前的平臺工具組，或安裝較舊的工具組，並將專案建立為未變更。 如需詳細資訊，請參閱 [升級舊版 Visual C++ 的專案](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) ，並 [在 Visual Studio 中使用原生多目標來建立舊專案](../../porting/use-native-multi-targeting.md)。

### <a name="retail-debug-or-platform-specific-libraries"></a>零售、偵測或平臺特定程式庫

當您第一次建立新的目標平臺或設定（例如零售或 ARM64）時，可能會發生此錯誤。 在 IDE 中，確認已安裝 [[一般] 屬性頁](../../build/reference/general-property-page-project.md)中指定的**平臺工具**組和**Windows SDK 版本**。 此外，請確認 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)中指定的連結**庫目錄**中有提供所需的程式庫。 檢查每個設定的屬性，例如 Debug、Retail、x86 或 ARM64。 如果有一個組建可以運作，但另一個沒有，請比較兩者的設定。 安裝任何遺漏的必要工具和程式庫。

### <a name="the-vccorliblib-library"></a>Vccorlib.h .lib 程式庫

針對通用 Windows (UWP) 應用程式或元件，並沒有可減輕 Spectre 的程式庫。 如果錯誤訊息包含 *vccorlib.h*，您可能已在 UWP 專案中啟用 [/Qspectre](../../build/reference/qspectre.md) 。 停用 **/Qspectre** 編譯器選項以修正此問題。 在 Visual Studio 中，變更 **Spectre 緩和** 屬性。 您可在 [專案屬性頁] 對話方塊的 [ **c/c + +** 程式  >  **代碼產生**] 頁面中找到它。 **Property Pages**

### <a name="libraries-in-projects-from-online-or-other-sources"></a>專案中來自線上或其他來源的程式庫

如果您建立的專案是從另一部電腦複製，則程式庫安裝位置可能會不同。 針對命令列組建，請確認已正確設定組建的 LIB 環境變數和程式庫路徑。 在 Visual Studio 中，您可以在專案的屬性頁中，查看及編輯目前設定的程式庫路徑。 在 [ **VC + + 目錄** ] 頁面中，選擇 [連結 **庫目錄** ] 屬性的下拉式清單控制項，然後選擇 [ **編輯**]。 [連結**庫目錄**] 對話方塊的 [**評估值**] 區段會列出目前搜尋程式庫檔案的路徑。 更新這些路徑以指向您的本機程式庫。

### <a name="updated-windows-sdk-libraries"></a>更新 Windows SDK 程式庫

當 Windows SDK 的 Visual Studio 路徑已過期時，就會發生這個錯誤。 如果您安裝較新的 Windows SDK，而不是 Visual Studio 安裝程式，就可能會發生此問題。 若要在 IDE 中修正此問題，請更新 [ [VC + + 目錄] 屬性頁](../../build/reference/vcpp-directories-property-page.md)中指定的路徑。 在路徑中設定版本，以符合新的 SDK。 如果您使用開發人員命令提示字元，請使用新的 SDK 路徑來更新初始化環境變數的批次檔。 您可以使用 Visual Studio 安裝程式來安裝更新的 Sdk，以避免此問題。

## <a name="cant-open-a-third-party-library-file"></a>無法開啟協力廠商程式庫檔案

這個問題有幾個常見的原因：

- 程式庫檔案的路徑可能不正確，或不是以雙引號括住。 或者，您可能未將它指定給連結器。

- 您可能已安裝32位版本的程式庫，但您正在建立64位或其他方法。

- 程式庫可能會相依于未安裝的其他程式庫。

若要修正命令列組建的路徑問題，請確認已設定 LIB 環境變數。 請確定它包含您所使用之所有程式庫的路徑，以及您所建立之每個設定的路徑。 在 IDE 中，[ **VC + + 目錄**連結  >  **庫目錄**] 屬性會設定程式庫路徑。 針對您所建立的每個設定，請確定此處所列的所有包含您所需程式庫的目錄。

您可能需要提供覆寫標準程式庫目錄的程式庫目錄。 在命令列上，使用 [/LIBPATH](../../build/reference/libpath-additional-libpath.md) 選項。 在 IDE 中，使用專案的 [設定**屬性] > 連結器**的 [一般] 屬性頁中的 [其他 > 連結**庫目錄**] 屬性。

請務必安裝您所建立之設定所需的每個程式庫版本。 請考慮使用 [vcpkg](../../build/vcpkg.md) 套件管理公用程式，將許多常見程式庫的安裝和設定自動化。 如果可以，最好建立自己的協力廠商程式庫複本。 然後，您會確定擁有所有程式庫的本機相依性，並針對與您專案相同的設定建立。

## <a name="cant-open-a-file-built-by-your-project"></a>無法開啟您的專案所建立的檔案

如果在連結器嘗試存取時， *檔案名* 尚不存在，您可能會看到此錯誤。 當某個專案相依于方案中的另一個專案時，就會發生這種情況，但專案會以錯誤的順序建立。 若要修正此問題，請確定已在使用該檔案的專案中設定您的專案參考。 然後，遺失的檔案會在需要時建立。 如需詳細資訊，請參閱 [在 Visual Studio c + + 專案中加入參考](../../build/adding-references-in-visual-cpp-projects.md) ，以及 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。

## <a name="cannot-open-file-cprogramobj"></a>無法開啟檔案 ' C： \\ Program .obj '

如果您在錯誤訊息中看到檔案名 *C： \\ Program* ，請以雙引號括住您的程式庫路徑。 當以 *C： \\ Program Files* 開頭的解除包裝路徑傳遞給連結器時，就會發生此錯誤。 未包裝的路徑也可能會造成類似的錯誤。 通常，它們會在磁片磁碟機的根目錄中顯示非預期的 .obj 檔。

若要針對命令列組建修正此問題，請檢查 [/LIBPATH](../../build/reference/libpath-additional-libpath.md) 選項參數。 此外，請檢查 LIB 環境變數中指定的路徑，以及命令列上指定的路徑。 請務必使用雙引號括住任何包含空格的路徑。

若要在 IDE 中修正此問題，請視需要在專案的下列屬性中新增雙引號：

- [Configuration Properties > VC + + 目錄](../../build/reference/vcpp-directories-property-page.md)屬性頁的 [連結**庫目錄**] 屬性

- 設定屬性中的 [ **其他程式庫目錄** ] 屬性 **> 連結器 > [一般** ] 屬性頁，

- 設定**屬性 > 連結器**的 [其他相依性 **]** 屬性 > 輸入屬性頁。

## <a name="other-common-issues"></a>其他常見問題

### <a name="path-or-filename-issues"></a>路徑或檔案名問題

當指定給連結器的程式庫檔案名或路徑不正確時，就會發生此錯誤。 或者，當路徑有不正確磁片磁碟機規格時。 查看命令列或任何 [#pragma 批註 ( lib、"library_name" ) ](../../preprocessor/comment-c-cpp.md) 指示詞的問題。 檢查您的拼寫和副檔名，並確認檔案存在於指定的位置。

### <a name="parallel-build-synchronization"></a>平行組建同步處理

如果您使用的是平行組建選項，Visual Studio 可能已在另一個執行緒上鎖定該檔案。 若要修正此問題，請確認相同的程式碼物件或程式庫不是在多個專案中建立的。 使用組建相依性或專案參考，在您的專案中挑選內建的二進位檔。

### <a name="additional-dependencies-specified-in-the-ide"></a>在 IDE 中指定的其他相依性

當您直接在 [其他相依性 **]** 屬性中指定個別的程式庫時，請使用空格來分隔程式庫名稱。 請勿使用逗號或分號。 如果您使用 [ **編輯** ] 功能表項目來開啟 [ **其他** 相依性] 對話方塊，請使用分行符號來分隔名稱，而不是逗號、分號或空格。 當您在 [連結 **庫目錄** ] 和 [ **其他程式庫目錄** ] 對話方塊中指定程式庫路徑時，也請使用新的

### <a name="paths-that-are-too-long"></a>路徑太長

當 *檔案名* 的路徑擴充至超過260個字元時，您可能會看到此錯誤。 如有需要，請重新排列您的目錄結構，或縮短資料夾和檔案名以縮短路徑。

### <a name="files-that-are-too-large"></a>檔案太大

發生此錯誤的原因可能是檔案太大。 程式庫或物件檔案大小超過 1 gb，可能會導致32位連結器發生問題。 解決此問題的可能原因是使用64位工具組。 如需有關如何在命令列使用64位工具組的詳細資訊，請參閱 [如何：在命令列上啟用64位 Visual C++ 工具](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)組。 如需如何在 IDE 中使用64位工具組的相關資訊，請參閱搭配 [使用 MSBuild 與64位編譯器和工具](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project)。 另請參閱這篇 Stack Overflow 文章： [如何讓 Visual Studio 使用原生 amd64 工具鏈](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055)。

### <a name="incorrect-file-permissions"></a>檔案許可權不正確

如果您的檔案許可權不足，無法存取 *檔案名*，就會發生這個錯誤。 如果您使用一般使用者帳戶存取受保護系統目錄中的程式庫檔案，就可能會發生此問題。 或者，如果您使用的檔案是從其他仍已設定原始許可權的使用者所複製。 若要修正此問題，請將檔案移至可寫入的專案目錄。 如果移動的檔案具有無法存取的許可權，請在系統管理員命令視窗中執行 takeown.exe 命令以取得檔案的擁有權。

### <a name="insufficient-disk-space"></a>磁碟空間不足

當您沒有足夠的磁碟空間時，就會發生此錯誤。 連結器在幾種情況下會使用暫存檔。 即使您有足夠的磁碟空間，大型連結也可以耗盡或分割可用磁碟空間。 請考慮使用 [/opt (優化) ](../../build/reference/opt-optimizations.md) 選項;執行可轉移的 COMDAT 刪除會多次讀取所有的物件檔案。

### <a name="problems-in-the-tmp-environment-variable"></a>TMP 環境變數中的問題

如果 *檔案名* 名稱為 .lnk*nnn*，則是由連結器為暫存檔案產生的檔案名。 TMP 環境變數中指定的目錄不存在。 或者，您可以為 TMP 環境變數指定一個以上的目錄。 TMP 環境變數只應指定一個目錄路徑。

## <a name="help-my-issue-isnt-listed-here"></a>說明，我的問題未列在這裡！

如果此處所列的問題都不適用，您可以使用 Visual Studio 中的意見反應工具來取得協助。 在 IDE 中，移至功能表列並選擇 [說明] **> [傳送意見**反應] > [回報問題]。 或者，您可以使用 [說明] > 傳送意見反應來提交建議 **> 傳送建議**。 您也可以使用 Visual Studio c + + [開發人員社群](https://developercommunity.visualstudio.com/spaces/62/index.html)) 網站。 您可以使用它來搜尋問題的答案，並尋求協助。 如需詳細資訊，請參閱 [如何報告 Visual C++ 工具組或檔的問題](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果您發現有新的方法可以修正此問題，我們應該新增至此文章，請讓我們知道。 您可以使用 **此頁面**下方的按鈕來傳送意見反應給我們。 您可以使用它在 [c + + 檔 GitHub](https://github.com/MicrosoftDocs/cpp-docs/issues)存放庫中建立新的問題。 感謝您！
