---
title: Windows 桌面精靈
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 47984b4c4416bf129efb226381fe778659aa16ca
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503520"
---
# <a name="windows-desktop-wizard"></a>Windows 桌面精靈

Windows Desktop Wizard 會取代 Visual Studio 2017 和更新版本中的 Win32 應用程式 Wizard。 此 wizard 可讓您建立四種類型的 c + + 專案 (列在下表中的標題) 。 在每個案例中，您都可以為開啟的專案類型指定適合的其他選項。

   ![Windows 桌面精靈](media/windows-desktop-wizard.png)

下表指出每種應用程式類型可使用的選項。

|支援類型|主控台應用程式|可執行檔 (Windows) 應用程式|動態連結程式庫|靜態程式庫|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**空白專案**|是|是|是|否|
|**匯出符號**|否|否|是|否|
|**先行編譯標頭檔**|否|否|否|是|
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
|**主控台應用程式**|建立主控台應用程式 (Console Application)。 Visual C++ [執行時間程式庫](../c-runtime-library/c-run-time-library-reference.md) 也會使用標準 i/o 函式（例如和），從主控台視窗提供輸出和 `printf_s()` 輸入 `scanf_s()` 。 主控台應用程式沒有圖形化使用者介面。 它會編譯成 .exe 檔案，而且可以從命令列以獨立應用程式的形式執行。<br /><br /> 您可以將 MFC 和 ATL 支援新增至主控台應用程式。|
|**Windows 應用程式**|建立 Win32 程式。 Win32 程式是以 C 或 c + + 撰寫的可執行應用程式 (EXE) 以 C 或 c + + 撰寫，並使用 WIN32 API 的呼叫來建立圖形化使用者介面。<br /><br /> 您無法將 MFC 或 ATL 支援新增至 Windows 應用程式。|
|**動態連結程式庫**|建立 Win32 動態連結程式庫 (DLL) 。 Win32 DLL 是以 C 或 c + + 撰寫的二進位檔案，它會使用 WIN32 API 的呼叫，而不是 MFC 類別，也可作為可由多個應用程式同時使用的共用函式程式庫。<br /><br /> 您無法將 MFC 或 ATL 支援新增至使用此 wizard 建立的 DLL 應用程式，但您可以選擇 [ **新增 > 專案 > MFC dll**] 來建立 mfc dll。|
|**靜態程式庫**|建立靜態程式庫。 靜態程式庫是一種檔案，其中包含物件及其函式和資料，可在建立可執行檔時連結至您的程式。 本主題說明如何建立靜態程式庫的入門檔案和 [專案屬性](../build/reference/property-pages-visual-cpp.md) 。 靜態程式庫檔案提供下列優點：<br /><br />-如果您正在處理的應用程式會呼叫 WIN32 API 而非 MFC 類別，Win32 靜態程式庫就很有用。<br />-無論您的 Windows 應用程式的其餘部分是以 C 或 c + + 撰寫，連結程式都相同。<br />-您可以將靜態程式庫連結至以 MFC 為基礎的程式或非 MFC 程式。|

## <a name="additional-options"></a>其他選項

定義應用程式的支援和選項，視其類型而定。

|選項|描述|
|------------|-----------------|
|**空白專案**|指定專案檔案是空白的。 如果您有一組原始程式碼檔 (例如 .cpp 檔、標頭檔、圖示、工具列、對話方塊等) ，而且想要在 Visual C++ 開發環境中建立專案，則必須先建立空白專案，然後將檔案加入至專案。<br /><br /> 靜態程式庫專案無法使用這個選項。|
|**匯出符號**|指定 DLL 專案匯出符號。|
|**先行編譯標頭檔**|指定靜態程式庫專案使用預先編譯的標頭。|
|** (SDL) 檢查的安全性開發週期**|如需 SDL 的詳細資訊，請參閱 [Microsoft 安全性開發生命週期 (SDL) 流程指引](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>新增的一般標頭：

針對 Visual C++ 中提供的其中一個程式庫新增支援。

|選項|描述|
|------------|-----------------|
|**ATL**|在 Active Template Library (ATL) 的類別中建立專案支援。 僅限 Win32 主控台應用程式。<br /><br /> **注意** 此選項不表示支援使用 ATL 程式碼嚮導來新增 ATL 物件。 您只能將 ATL 物件加入至 ATL 專案或具有 ATL 支援的 MFC 專案。|
|**MFC**|以 MFC) 程式庫 (MFC 的專案支援為基礎。 僅限 Win32 主控台應用程式和靜態程式庫。|

## <a name="remarks"></a>備註

一旦建立了 Windows 桌面應用程式，就可以使用 [泛型](../ide/adding-a-generic-cpp-class.md#generic-c-class-wizard) 程式碼精靈加入泛型 C++ 類別。 您可以加入其他項目，例如 HTML 檔案、標頭檔、資源或文字檔案。

> [!NOTE]
> 您不能加入 ATL 類別，而 MFC 類別只能加入支援 MFC 的那些 Windows 桌面應用程式類型 (請見上表)。

您可以在 **方案總管**中檢視精靈為專案建立的檔案。 如需 wizard 針對您的專案所建立之檔案的詳細資訊，請參閱專案產生的檔案 `ReadMe.txt` 。 如需檔案類型的詳細資訊，請為 [Visual Studio c + + 專案建立的檔案類型](../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的 C++ 專案類型](../build/reference/visual-cpp-project-types.md)
