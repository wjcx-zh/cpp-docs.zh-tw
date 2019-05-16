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
ms.openlocfilehash: a434a329febc38d6a46881dcabba6b05a402fbca
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708058"
---
# <a name="windows-desktop-wizard"></a>Windows 傳統式精靈

Windows Desktop 精靈 會取代 Win32 應用程式精靈 在 Visual Studio 2017 和更新版本。 此精靈可讓您建立的四種類型的任何C++（列於下表中的標題） 的專案。 在每個案例中，您都可以為開啟的專案類型指定適合的其他選項。 

   ![Windows 傳統式精靈](media/windows-desktop-wizard.png)

下表指出每種應用程式類型可使用的選項。

|支援類型|主控台應用程式|可執行檔 (Windows) 應用程式|動態連結程式庫|靜態程式庫|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**空專案**|是|是|是|否|
|**匯出符號**|否|否|[是]|否|
|**先行編譯標頭**|否|否|否|是|
|**ATL 支援**|是|否|否|否|
|**MFC 支援**|是|否|否|是|

## <a name="overview"></a>總覽

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
|**主控台應用程式**|建立主控台應用程式 (Console Application)。 以開發主控台程式[主控台函式](https://msdn.microsoft.com/library/ms813137.aspx)，提供在主控台視窗中的字元模式支援。 視覺效果C++[執行階段程式庫](../c-runtime-library/c-run-time-library-reference.md)也提供輸出，並從主控台視窗，使用標準 I/O 函式，這類輸入`printf_s()`並`scanf_s()`。 主控台應用程式有沒有圖形化使用者介面。 它會編譯為.exe 檔案，並可當做獨立的應用程式，從命令列來執行。<br /><br /> 您可以新增 MFC 與 ATL 支援新增至主控台應用程式。|
|**Windows 應用程式**|建立 Win32 程式。 Win32 程式是以 C 撰寫的可執行檔應用程式 (EXE) 或C++，來建立圖形化使用者介面中使用 Win32 API 的呼叫。<br /><br /> 您無法新增 MFC 或 ATL 支援加入至 Windows 應用程式。|
|**動態連結程式庫**|建立 Win32 動態連結程式庫 (DLL)。 Win32 DLL 是以 C 撰寫的二進位檔案，或C++，會使用呼叫 Win32 API，而不是 MFC 類別，做為共用程式庫的多個應用程式可以同時使用的函式。<br /><br /> 您無法使用此精靈，來建立 DLL 應用程式中加入 MFC 或 ATL 的支援，但您可以建立 MFC DLL 藉由選擇**新增 > 專案 > MFC DLL**。|
|**靜態程式庫**|建立靜態程式庫。 靜態程式庫是包含物件和其功能與資料，用來建置可執行檔時，連結到您的程式檔案。 本主題說明如何建立初學者檔案和[專案屬性](../build/reference/property-pages-visual-cpp.md)靜態程式庫。 靜態程式庫檔案提供下列優點：<br /><br />-如果您正在使用的應用程式呼叫 Win32 API，而不是 MFC 類別非常有用 Win32 靜態程式庫。<br />-連結的程序是相同，無論您的 Windows 應用程式的其餘部分以 C 撰寫或在C++。<br />-您可以在以 MFC 為基礎的程式或非 MFC 程式連結的靜態程式庫。|

## <a name="additional-options"></a>其他選項

定義支援和應用程式，根據其類型的選項。

|選項|描述|
|------------|-----------------|
|**空專案**|指定的專案檔案空白。 如果您有一組的原始程式檔 （例如.cpp 檔案、 標頭檔、 圖示、 工具列、 對話方塊和等等），而且想要建立視覺效果中的專案C++開發環境中，您必須先建立空白的專案，然後將檔案新增至專案。<br /><br /> 此選項不適用於靜態程式庫專案。|
|**匯出符號**|指定 DLL 專案匯出的符號。|
|**先行編譯標頭**|指定靜態程式庫專案會使用預先編譯的標頭。|
|**安全性開發生命週期 (SDL) 檢查**|如需有關 SDL 的詳細資訊，請參閱[Microsoft 安全性開發生命週期 (SDL) 流程指引](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>新增通用標頭：

新增視覺效果中所提供的程式庫的其中一個支援C++。

|選項|描述|
|------------|-----------------|
|**ATL**|會建置類別 Active Template Library (ATL) 的專案支援。 Win32 主控台應用程式只。<br /><br /> **請注意**這個選項不會指出加入 ATL 物件使用 ATL 程式碼精靈的支援。 您可以加入 ATL 物件到 ATL 專案或 ATL 與 MFC 專案支援。|
|**MFC**|會建置 Microsoft Foundation Class (MFC) 程式庫的專案支援。 適用於 Win32 主控台應用程式和靜態程式庫。|

## <a name="remarks"></a>備註

一旦建立了 Windows 桌面應用程式，就可以使用 [泛型](../ide/generic-cpp-class-wizard.md) 程式碼精靈加入泛型 C++ 類別。 您可以加入其他項目，例如 HTML 檔案、標頭檔、資源或文字檔案。

> [!NOTE]
> 您不能加入 ATL 類別，而 MFC 類別只能加入支援 MFC 的那些 Windows 桌面應用程式類型 (請見上表)。

您可以在 **方案總管**中檢視精靈為專案建立的檔案。 更多精靈為您的專案所建立之檔案的相關資訊，請參閱專案所產生的檔案， `ReadMe.txt`。 如需有關檔案類型[適用於 Visual Studio 建立的檔案類型C++專案](../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[C++在 Visual Studio 中的專案類型](../build/reference/visual-cpp-project-types.md)