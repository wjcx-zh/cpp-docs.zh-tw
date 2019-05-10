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
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524790"
---
# <a name="mfc-library-versions"></a>MFC 程式庫版本

MFC 程式庫有版本支援 ANSI 單一位元組和多位元組字元集 (MBCS) 程式碼，以及支援 （編碼為 UTF-16LE Windows 原生字元集） 的 Unicode 版本。 為靜態程式庫或共用的 DLL 使用每個 MFC 版本。 另外還有省去了 MFC 控制項的大小非常敏感，而且不需要這些控制項的應用程式的對話方塊，較小 MFC 靜態程式庫版本。 MFC 程式庫是適用於這兩個偵錯和發行版本，針對支援的架構，包括 x86、 x64 和 ARM 處理器。 您可以建立兩個應用程式 （.exe 檔） 和任何版本的 MFC 程式庫的 Dll。 有一組針對源自於 managed 程式碼與編譯的 MFC 程式庫。 MFC 的共用 Dll 包含版本號碼來表示程式庫的二進位相容性。

## <a name="automatic-linking-of-mfc-library-versions"></a>MFC 程式庫版本的自動連結

MFC 標頭檔會自動判斷正確版本的 MFC 程式庫，若要連結，根據您的建置環境中所定義的值。 MFC 標頭檔新增編譯器指示詞，指示連結器連結特定版本的 MFC 程式庫。

例如，AFX 」。H 標頭檔會指示連結器連結完整靜態、 有限靜態，或共用的 DLL 版本;ANSI/MBCS 或 Unicode 版本;和偵錯或零售版本，視您的組建組態而定：

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

MFC 標頭檔也包含所有必要的程式庫，包括 MFC 程式庫、 Win32 程式庫、 OLE 程式庫，從範例建置的 OLE 程式庫、 ODBC 程式庫等等所連結的指示詞。

## <a name="ansi-mbcs-and-unicode"></a>ANSI、 MBCS 和 Unicode

ANSI/MBCS MFC 程式庫版本支援這兩個單一位元組字元集的 ASCII，例如，多位元組字元集 (SHIFT-JIS) 等。 MFC Unicode 程式庫版本支援 Unicode，其-16LE 寬字元的編碼格式。 使用 utf-8 編碼的 Unicode 支援 MFC 的 ANSI/MBCS 程式庫版本。

若要設定您的專案組態，以在 IDE 中使用單一位元組、 多位元組，或寬字元 Unicode 字串和字元支援，請使用**專案屬性**對話方塊。 在 **組態屬性** > **一般**頁面上，將**字元集**屬性**未設定**使用單一位元組字元集。 將屬性設定為**使用多位元組字元集**若要使用多位元組字元集，或**使用 Unicode 字元集**使用 Unicode 編碼為 utf-16。

MFC 專案使用的前置處理器符號\_表示 utf-16 寬字元 Unicode 支援的 UNICODE 和\_表示 MBCS 的 MBCS 支援。 這些選項是互斥的專案中。

## <a name="mfc-static-library-naming-conventions"></a>MFC 靜態程式庫命名慣例

Mfc 靜態程式庫會使用下列命名慣例。 程式庫名稱的格式如下

> <em>u</em>AFX<em>cd</em>.LIB

其中顯示為斜體小寫的字母是指定名稱的預留位置，其意義如下表所示：

|指定名稱|值和意義|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) 或 Unicode (U);省略版本，而 MFC 對話方塊中的控制項|
|*C*|使用 MFC 控制項對話方塊 (CW) 中，或不 (NMCD) 的版本|
|*d*|偵錯或發行：D = 偵錯;省略版本規範|

下表所列的所有程式庫都包含預先建置支援的建置架構的 \atlmfc\lib 目錄中。

|程式庫|描述|
|-------------|-----------------|
|NAFXCW.LIB|MFC 靜態連結程式庫，發行版本|
|NAFXCWD.LIB|MFC 靜態連結程式庫，偵錯版本|
|UAFXCW.LIB|MFC 靜態連結程式庫 (支援 Unicode)，發行版本|
|UAFXCWD.LIB|MFC 靜態連結程式庫 (支援 Unicode)，偵錯版本|
|AFXNMCD.LIB|不含 MFC 對話方塊控制項，發行版本的 MFC 靜態連結程式庫|
|AFXNMCDD.LIB|不含 MFC 對話方塊控制項，偵錯版本的 MFC 靜態連結程式庫|

具有相同的主檔名和副檔名為.pdb 的偵錯工具檔案也可供每個靜態程式庫。

## <a name="mfc-shared-dll-naming-conventions"></a>MFC 的共用 DLL 命名慣例

MFC 的共用 Dll 也遵循結構化的命名慣例。 這可讓您更輕鬆地知道哪一個 DLL 或程式庫，您應該使用用途。

MFC Dll 已*版本*數字，指出二進位碼相容性。 使用具有相同的版本與您其他的程式庫和編譯器工具組，以確保在專案中的相容性的 MFC Dll。

|DLL|描述|
|---------|-----------------|
|MFC*version*.DLL|MFC DLL、 ANSI 或 MBCS 版本的版本|
|MFC*version*U.DLL|MFC DLL，Unicode 發行版本|
|MFC*version*D.DLL|MFC DLL，ANSI 或 MBCS 偵錯版本|
|MFC*version*UD.DLL|MFC DLL，Unicode 偵錯版本|
|MFCM*version*.DLL|使用 Windows Form 控制項，MFC DLL ANSI 或 MBCS 發行版本|
|MFCM*version*U.DLL|使用 Windows Form 控制項，Unicode 版本的 MFC DLL|
|MFCM*version*D.DLL|使用 Windows Form 控制項，MFC DLL ANSI 或 MBCS 偵錯版本|
|MFCM*version*UD.DLL|使用 Windows Form 控制項，Unicode 偵錯版本的 MFC DLL|

建置應用程式或 MFC 擴充 Dll 使用這些共用的 Dll 所需的匯入程式庫有相同的基底名稱與 DLL，但有副檔名為.lib 檔案。 當您使用共用的 Dll 時，必須仍與您的程式碼; 連結小型的靜態程式庫此程式庫名為 MFCS*版本*{U} {D}.lib。

如果您以動態方式連結至 MFC 的共用 DLL 版本是否從應用程式，或從 MFC 擴充 DLL，您必須包含相符的 MFC*版本*。DLL 或 MFC*版本*U.DLL 時部署您的產品。

如需清單視覺效果的C++Dll，可以與您的應用程式發佈，請參閱[Microsoft Visual Studio 2017 和 Microsoft Visual Studio 2017 SDK （包含公用程式與 BuildServer 檔案） 的可散發程式碼](/visualstudio/productinfo/2017-redistribution-vs)或[Visual Studio 2019 的可散發程式碼](/visualstudio/releases/2019/redistribution)。

如需有關在 MFC 的 MBCS 和 Unicode 支援的詳細資訊，請參閱 < [Unicode 和多位元組字元集 (MBCS) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="dynamic-link-library-support"></a>動態連結程式庫支援

您可以使用其中一個靜態或共用動態 MFC 程式庫來建立可由 MFC 和非 MFC 可執行檔的 Dll。 這些稱為 「 標準 Dll 」 或 「 標準 MFC Dll 」，以便區別 MFC 擴充 Dll，僅能使用 MFC 應用程式和 MFC Dll。 使用 MFC 靜態程式庫所建置的 DLL 有時稱為 USRDLL 在較舊的參考，因為 MFC DLL 專案定義的前置處理器符號 **\_USRDLL**。 使用 MFC 共用 Dll 的 DLL 有時稱為 AFXDLL 在較舊的參考，因為它會定義前置處理器符號 **\_AFXDLL**。

當您建立 DLL 專案，藉由連結至 MFC 的靜態程式庫時，而 MFC 的共用 Dll 不可以部署您的 DLL。 匯入程式庫 MFC DLL 專案的連結時*版本*。LIB 或 MFC*版本*U.LIB，您必須部署比對 MFC 共用 DLL 的 MFC*版本*。DLL 或 MFC*版本*U.DLL 連同您的 DLL。 如需詳細資訊，請參閱 < [Dll](../build/dlls-in-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)
