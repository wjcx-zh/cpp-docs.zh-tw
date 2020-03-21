---
title: Windows 傳統式精靈
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 3d8be0cc33e0435bc5a18191303dbbc91277de0b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075457"
---
# <a name="windows-desktop-wizard"></a>Windows 傳統式精靈

Windows 桌面 Wizard 取代了 Visual Studio 2017 和更新版本中的 Win32 應用程式精靈。 此嚮導可讓您建立四種類型的C++專案（列于下表的標題中）。 在每個案例中，您都可以為開啟的專案類型指定適合的其他選項。

   ![Windows 傳統式精靈](media/windows-desktop-wizard.png)

下表指出每種應用程式類型可使用的選項。

|支援類型|主控台應用程式|可執行檔 (Windows) 應用程式|動態連結程式庫|靜態程式庫|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**空專案**|是|是|是|否|
|**匯出符號**|否|否|是|否|
|**先行編譯標頭**|否|否|否|是|
|**ATL 支援**|是|否|否|否|
|**MFC 支援**|是|否|否|是|

## <a name="overview"></a>概觀

這個精靈頁面說明目前適用於您建立之 Win32 應用程式的專案設定。 根據預設，設定下列選項：

- 專案是 Windows 應用程式。

- 專案不是空的。

- 專案不包含匯出符號。

- 專案不使用先行編譯的標頭檔 (這個選項僅適用於靜態程式庫專案)。

- 專案對 MFC 或 ATL 都不支援。

## <a name="application-type"></a>應用程式類型

建立指定的應用程式類型。

|選項|描述|
|------------|-----------------|
|**主控台應用程式**|建立主控台應用程式 (Console Application)。 Visual C++ [執行時間程式庫](../c-runtime-library/c-run-time-library-reference.md)也會從具有標準 i/o 功能的主控台視窗（例如 `printf_s()` 和 `scanf_s()`）提供輸出和輸入。 主控台應用程式沒有圖形化使用者介面。 它會編譯成 .exe 檔案，並可從命令列以獨立應用程式的形式執行。<br /><br /> 您可以將 MFC 和 ATL 支援加入至主控台應用程式。|
|**Windows 應用程式**|建立 Win32 程式。 Win32 程式是以 C 或C++撰寫的可執行應用程式（EXE），使用 WIN32 API 的呼叫來建立圖形化使用者介面。<br /><br /> 您無法將 MFC 或 ATL 支援新增至 Windows 應用程式。|
|**動態連結程式庫**|建立 Win32 動態連結程式庫（DLL）。 Win32 DLL 是以 C 或C++撰寫的二進位檔案，它會使用 WIN32 API 的呼叫，而不是 MFC 類別，並作為可供多個應用程式同時使用的函式共用程式庫。<br /><br /> 您無法將 MFC 或 ATL 支援新增至使用此 wizard 所建立的 DLL 應用程式，但您可以選擇 新增  **> 專案 > MFC dll** 來建立 mfc dll。|
|**靜態程式庫**|建立靜態程式庫。 靜態程式庫是一個檔案，其中包含在建立可執行檔時連結至程式的物件及其功能和資料。 本主題說明如何建立靜態程式庫的起始檔案和[專案屬性](../build/reference/property-pages-visual-cpp.md)。 靜態程式庫檔案提供下列優點：<br /><br />-如果您正在處理的應用程式會呼叫 WIN32 API，而不是 MFC 類別，Win32 靜態程式庫就很有用。<br />-不論 Windows 應用程式的其餘部分是以 C 或撰寫而成，連結進程都相同C++。<br />-您可以將靜態程式庫連結至以 MFC 為基礎的程式或非 MFC 程式。|

## <a name="additional-options"></a>其他選項

定義應用程式的支援和選項，視其類型而定。

|選項|描述|
|------------|-----------------|
|**空專案**|指定專案檔案為空白。 如果您有一組原始程式碼檔案（例如 .cpp 檔案、標頭檔、圖示、工具列、對話方塊等等），而且想要在視覺化C++開發環境中建立專案，您必須先建立空白專案，然後將檔案加入至專案。<br /><br /> 靜態程式庫專案無法使用此選項。|
|**匯出符號**|指定 DLL 專案匯出符號。|
|**先行編譯標頭**|指定靜態程式庫專案使用預先編譯的標頭。|
|**安全性開發週期（SDL）檢查**|如需 SDL 的詳細資訊，請參閱[Microsoft 安全性開發週期 (SDL) （SDL）流程指引](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>新增的通用標頭：

為 Visual C++中提供的其中一個程式庫加入支援。

|選項|描述|
|------------|-----------------|
|**ATL**|建置於 Active Template Library （ATL）中類別的專案支援。 僅適用于 Win32 主控台應用程式。<br /><br /> **注意**此選項不表示支援使用 ATL 程式碼嚮導來新增 ATL 物件。 您只能將 ATL 物件新增至 atl 專案或具有 ATL 支援的 MFC 專案。|
|**MFC**|建置於 Microsoft Foundation Class （MFC）程式庫的專案支援中。 僅適用于 Win32 主控台應用程式和靜態程式庫。|

## <a name="remarks"></a>備註

一旦建立了 Windows 桌面應用程式，就可以使用 [泛型](../ide/generic-cpp-class-wizard.md) 程式碼精靈加入泛型 C++ 類別。 您可以加入其他項目，例如 HTML 檔案、標頭檔、資源或文字檔案。

> [!NOTE]
> 您不能加入 ATL 類別，而 MFC 類別只能加入支援 MFC 的那些 Windows 桌面應用程式類型 (請見上表)。

您可以在 **方案總管**中檢視精靈為專案建立的檔案。 如需 wizard 為您的專案建立之檔案的詳細資訊，請參閱專案產生的檔案 `ReadMe.txt`。 如需檔案類型的詳細資訊，請閱讀[為 Visual Studio C++專案所建立的檔案類型](../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++ 專案類型](../build/reference/visual-cpp-project-types.md)