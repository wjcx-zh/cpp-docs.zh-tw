---
title: MFC 程式庫版本
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: b8e32366d9ff43bd6e5770f64f0ba9d8bf6e56ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856796"
---
# <a name="mfc-library-versions"></a>MFC 程式庫版本

MFC 程式庫提供支援 ANSI 單一位元組和多位元組字元集（MBCS）程式碼的版本，以及支援 Unicode 的版本（編碼為 UTF-16LE，即 Windows 原生字元集）。 每個 MFC 版本都以靜態程式庫或共用 DLL 的形式提供。 還有一個較小的 MFC 靜態程式庫版本，它會針對對大小非常敏感且不需要這些控制項的應用程式，離開對話方塊的 MFC 控制項。 MFC 程式庫適用于支援的架構（包括 x86、x64 和 ARM 處理器）的「偵錯工具」和「發行」版本。 您可以使用任何版本的 MFC 程式庫來建立應用程式（.exe 檔案）和 Dll。 此外，也有一組編譯成與 managed 程式碼互動的 MFC 程式庫。 MFC 共用 Dll 包含版本號碼，以表示程式庫二進位相容性。

## <a name="automatic-linking-of-mfc-library-versions"></a>MFC 程式庫版本的自動連結

MFC 標頭檔會根據您的組建環境中定義的值，自動判斷要連結的 MFC 程式庫的正確版本。 MFC 標頭檔會新增編譯器指示詞，指示連結器連結至特定版本的 MFC 程式庫。

例如，AFX。H 標頭檔會指示連結器在 MFC 的完整靜態、受限靜態或共用 DLL 版本中連結。ANSI/MBCS 或 Unicode 版本;和 debug 或 retail 版本，視您的組建設定而定：

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

MFC 標頭檔也包含在所有必要程式庫中連結的指示詞，包括 MFC 程式庫、Win32 程式庫、OLE 程式庫、從範例所建立的 OLE 程式庫、ODBC 程式庫等等。

## <a name="ansi-mbcs-and-unicode"></a>ANSI、MBCS 和 Unicode

MFC ANSI/MBCS 程式庫版本同時支援單一位元組字元集（例如 ASCII）和多位元組字元集（例如，Shift-JIS）。 MFC Unicode 程式庫版本支援以 UTF UTF-16LE 寬字元編碼格式的 Unicode。 使用 MFC 的 ANSI/MBCS 程式庫版本，以進行 UTF-8 編碼的 Unicode 支援。

若要將專案設定設為在 IDE 中使用單一位元組、多位元組或寬字元的 Unicode 字串和字元支援，請使用 [**專案屬性**] 對話方塊。 在 [設定**屬性** > **一般**] 頁面中，將 [**字元集**] 屬性設為 [**不會設定**為使用單位元組字元集]。 將屬性設定為**使用多位元組字元集**，以使用多位元組字元集，或**使用 unicode 字元集**來使用 unicode 編碼為 utf-16。

MFC 專案會使用預處理器符號 \_UNICODE 來指示 UTF-16 寬字元 Unicode 支援，並 \_MBCS 來指示 MBCS 支援。 這些選項在專案中是互斥的。

## <a name="mfc-static-library-naming-conventions"></a>MFC 靜態程式庫命名慣例

MFC 的靜態程式庫會使用下列命名慣例。 程式庫名稱的格式如下

> <em>u</em>AFX<em>cd</em>。LIB

其中顯示為斜體小寫的字母是指定名稱的預留位置，其意義如下表所示：

|規範|值和意義|
|---------------|-------------------------|
|*u*|ANSI/MBCS （N）或 Unicode （U）;在對話方塊中省略不含 MFC 控制項的版本|
|*c*|對話方塊（CW）或不含（NMCD）中的 MFC 控制項版本|
|*d*|偵錯或發行：D=偵錯 (Debug)；省略指定名稱=發行 (Release)|

下表所列的所有程式庫都包含在支援的組建架構的 \atlmfc\lib 目錄中預先建立。

|程式庫|描述|
|-------------|-----------------|
|NAFXCW.LIB|MFC 靜態連結程式庫，發行版本|
|NAFXCWD.LIB|MFC 靜態連結程式庫，偵錯版本|
|UAFXCW.LIB|MFC 靜態連結程式庫 (支援 Unicode)，發行版本|
|UAFXCWD.LIB|MFC 靜態連結程式庫 (支援 Unicode)，偵錯版本|
|AFXNMCD.LIB|MFC 靜態程式庫（不含 MFC 對話方塊控制項，發行版本）|
|AFXNMCDD.LIB|MFC 靜態程式庫（不含 MFC 對話方塊控制項）、Debug 版本|

具有相同基底名稱和 .pdb 副檔名的偵錯工具檔案也適用于每個靜態程式庫。

## <a name="mfc-shared-dll-naming-conventions"></a>MFC 共用 DLL 命名慣例

MFC 共用 Dll 也會遵循結構化的命名慣例。 這可讓您更輕鬆地知道應該使用哪個 DLL 或程式庫來進行哪些用途。

MFC Dll 具有表示二進位相容性的*版本*號碼。 使用與其他程式庫和編譯器工具組具有相同版本的 MFC Dll，以確保專案內的相容性。

|DLL|描述|
|---------|-----------------|
|MFC*版本*。URLMON.DLL|MFC DLL、ANSI 或 MBCS 發行版本|
|MFC*版本*U .dll|MFC DLL，Unicode 發行版本|
|MFC*版本*d. .dll|MFC DLL、ANSI 或 MBCS Debug 版本|
|MFC*版本*UD。URLMON.DLL|MFC DLL，Unicode Debug 版本|
|MFCM VERSION U.DLL*版本*。URLMON.DLL|具有 Windows Forms 控制項、ANSI 或 MBCS 發行版本的 MFC DLL|
|MFCM VERSION U.DLL*版本*U .dll|具有 Windows Forms 控制項的 MFC DLL，Unicode 發行版本|
|MFCM VERSION U.DLL*版本*d. .dll|具有 Windows Forms 控制項、ANSI 或 MBCS Debug 版本的 MFC DLL|
|MFCM VERSION U.DLL*版本*UD。URLMON.DLL|具有 Windows Forms 控制項的 MFC DLL，Unicode Debug 版本|

建立應用程式所需的匯入程式庫或使用這些共用 Dll 的 MFC 延伸 Dll，其基底名稱與 DLL 相同，但副檔名為 .lib。 當您使用共用 Dll 時，小型靜態程式庫仍然必須與您的程式碼連結;此程式庫名為 MFCS*version*{U} {D} .lib。

如果您要動態連結至 MFC 的共用 DLL 版本，不論它是來自應用程式還是 MFC 延伸 DLL，您都必須包含相符的 MFC*版本*。當您部署產品時，DLL 或 MFC*版本*的 .dll。

如需可與您C++的應用程式一起散發的 Visual dll 清單，請參閱[Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 SDK （包含公用程式和 BuildServer 檔）](/visualstudio/productinfo/2017-redistribution-vs)的可散佈程式碼，或[用於 Visual Studio 2019](/visualstudio/releases/2019/redistribution)的可散發程式碼。

如需 MFC 中 MBCS 和 Unicode 支援的詳細資訊，請參閱[Unicode 和多位元組字元集（MBCS）支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="dynamic-link-library-support"></a>動態連結程式庫支援

您可以使用靜態或共用動態 MFC 程式庫來建立可供 MFC 和非 MFC 可執行檔使用的 Dll。 這些稱為「一般 Dll」或「一般 MFC Dll」，以便與只能由 MFC 應用程式和 MFC Dll 使用的 MFC 擴充 Dll 區別。 使用 MFC 靜態程式庫建立的 DLL 有時在較舊的參考中稱為 USRDLL，因為 MFC DLL 專案會定義預處理器符號 **\_USRDLL**。 使用 MFC 共用 Dll 的 DLL 有時在較舊的參考中稱為 AFXDLL，因為它會定義預處理器符號 **\_AFXDLL**。

當您藉由連結至 MFC 靜態程式庫來建立 DLL 專案時，可以不使用 MFC 共用 Dll 來部署您的 DLL。 當您的 DLL 專案連結至匯入程式庫 MFC*版本*時。LIB 或 MFC*版本*的 node.js，您必須部署相符的 MFC 共用 DLL mfc*版本*。DLL 或 MFC*版本*的 U l 與您的 dll 一起使用。 如需詳細資訊，請參閱[dll](../build/dlls-in-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)
