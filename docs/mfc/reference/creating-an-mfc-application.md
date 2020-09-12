---
title: 建立 MFC 應用程式
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 115ca6b4ab32482707cffd08ef575c93b2f3bfa9
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040089"
---
# <a name="creating-an-mfc-application"></a>建立 MFC 應用程式

MFC 應用程式以 MFC 程式庫為基礎，是 Windows 的可執行應用程式。 MFC 可執行檔通常分為五種類型：標準 Windows 應用程式、對話方塊、表單架構應用程式、Explorer 樣式的應用程式，以及網頁瀏覽器樣式的應用程式。 如需詳細資訊，請參閱

- [使用類別來編寫 Windows 應用程式](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [建立和顯示對話方塊](../../mfc/creating-and-displaying-dialog-boxes.md)

- [建立以表單為基礎的 MFC 應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [建立網頁瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

MFC 應用程式精靈可根據您在精靈中選取的選項，為任意類型的應用程式，產生適當的類別和檔案。

建立 MFC 應用程式最簡單的方式，就是在 Visual Studio 2019) 中使用 MFC 應用程式的 (Mfc 應用程式 **專案** 。 若要建立 MFC 主控台應用程式 (使用 MFC 程式庫，但在主控台視窗) 中執行的命令列程式，請使用 Windows 桌上出版 Wizard，然後選擇 [ **主控台應用程式** ] 和 [ **MFC 標頭** ] 選項。

::: moniker range=">=vs-2019"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>若要建立 MFC 表單或對話方塊架構應用程式

1. 從主功能表選擇 [檔案**File** > **新增** > **專案**]。
1. 在 [搜尋] 方塊中輸入「MFC」，然後從結果清單中選擇 [ **Mfc 應用程式** ]。
1. 視需要修改預設值，然後按 [ **建立** ] 以開啟 [ **MFC 應用程式]**。
1. 視需要修改設定值，然後按 **[完成]**。

如需詳細資訊，請參閱 [建立以表單為基礎的 MFC 應用程式](creating-a-forms-based-mfc-application.md)。

![Visual Studio 2019 MFC 應用程式精靈](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>若要建立 MFC 主控台應用程式

MFC 主控台應用程式是一個命令列程式，它會使用 MFC 程式庫，但會在主控台視窗中執行。

1. 從主功能表選擇 [檔案**File** > **新增** > **專案**]。
1. 在搜尋方塊中輸入 "Desktop"，然後從結果清單中選擇 [ **Windows 桌面 Wizard]** 。
1. 視需要修改專案名稱，然後按 **[下一步** ] 以開啟 **Windows Desktop Wizard**。
1. 選取 [ **MFC 標頭** ] 方塊，並視需要設定其他值，然後按 **[完成]**。

![Visual Studio 2019 Windows 桌面專案對話方塊](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=vs-2017"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>若要建立 MFC 表單或對話方塊架構應用程式

1. 從主功能表選擇 [檔案**File** > **新增** > **專案**]。
1. 在 [**已安裝**的範本**Visual C++**] 底下，選擇 [  >  **MFC/ATL**Visual C++]。 如果您看不到這些專案，請使用 Visual Studio 安裝程式加以新增。
1. 從中央窗格選擇 [ **MFC 應用程式** ]。
1. 視需要修改設定值，然後按 **[完成]**。

如需詳細資訊，請參閱 [建立以表單為基礎的 MFC 應用程式](creating-a-forms-based-mfc-application.md)。

![Visual Studio 2017 MFC 應用程式精靈](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>若要建立 MFC 主控台應用程式

MFC 主控台應用程式是一個命令列程式，它會使用 MFC 程式庫，但會在主控台視窗中執行。

1. 從主功能表選擇 [檔案**File** > **新增** > **專案**]。
1. 在 [ **已安裝** 的範本] 底下，選擇 [ **Visual C++** > **Windows 桌面**]。
1. 從中央窗格中選擇 [ **Windows 桌上型電腦]** 。
1. 視需要修改專案名稱，然後按 **[確定]** 以開啟 **Windows Desktop Wizard**。
1. 選取 [ **MFC 標頭** ] 方塊，並視需要設定其他值，然後按 **[完成]**。

![Visual Studio 2017 Windows 桌面專案對話方塊](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=vs-2015"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>若要建立 MFC 表單或對話方塊架構應用程式

1. 從主功能表選擇 [檔案**File** > **新增** > **專案**]。
1. 在 [ **已安裝** 的範本] 底下，選擇 [ **Visual C++** > **MFC**]。
1. 從中央窗格選擇 [ **MFC 應用程式** ]。
1. 按 **[下一步** ] 啟動 [ **MFC 應用程式]**。

如需詳細資訊，請參閱 [建立以表單為基礎的 MFC 應用程式](creating-a-forms-based-mfc-application.md)。

![Visual Studio 2015 MFC 應用程式精靈](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>若要建立 MFC 主控台應用程式

MFC 主控台應用程式是一個命令列程式，它會使用 MFC 程式庫，但會在主控台視窗中執行。

1. 從主功能表選擇 [檔案**File** > **新增** > **專案**]。
1. 在 [ **已安裝** 的範本] 底下，選擇 [ **Visual C++** > **Win32**]。
1. 從中央窗格選擇 [ **Win32 主控台應用程式** ]。
1. 視需要修改專案名稱，然後按 **[確定]**。
1. 在嚮導的第二個頁面上，選取 [ **新增 MFC 的通用標頭** ] 方塊，並視需要設定其他值，然後按 **[完成]**。

::: moniker-end

專案一旦建立完成之後，即可檢視在 [方案總管]**** 內建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[為 Visual Studio C++ 專案建立的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)
