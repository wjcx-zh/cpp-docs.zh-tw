---
title: 建立 MFC 應用程式
ms.date: 07/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 454a994da6db2841317d41ea1cdacfd36b0705e4
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606476"
---
# <a name="creating-an-mfc-application"></a>建立 MFC 應用程式

MFC 應用程式以 MFC 程式庫為基礎，是 Windows 的可執行應用程式。 建立 MFC 應用程式最簡單的方式, 是使用 MFC 應用程式精靈 (Visual Studio 2019 中的**Mfc 應用程式專案**)。 若要建立 MFC 主控台應用程式, 請使用 Windows 桌面 Wizard 並選擇 [**主控台應用程式**] 和 [ **MFC 標頭**] 選項。

> [!IMPORTANT]
>  Visual Studio Express 版本不支援 MFC 專案。

MFC 可執行檔通常分成五種類型: 標準 Windows 應用程式、對話方塊、表單架構應用程式、Explorer 樣式的應用程式, 以及網頁瀏覽器樣式的應用程式。 如需詳細資訊，請參閱：

- [使用類別來撰寫 Windows 應用程式](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [建立和顯示對話方塊](../../mfc/creating-and-displaying-dialog-boxes.md)

- [建立表單架構的 MFC 應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [建立網頁瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

MFC 應用程式精靈可根據您在精靈中選取的選項，為任意類型的應用程式，產生適當的類別和檔案。

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>若要使用 MFC 應用程式精靈建立 MFC 應用程式

1. 依照說明主題[建立C++主控台應用程式專案](../../get-started/tutorial-console-cpp.md)中的指示進行。

1. 在 [**新增專案**] 對話方塊中, 選取 [範本] 窗格中的 [ **MFC 應用程式**], 以開啟嚮導。

1. 使用[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)來定義應用程式設定。

    > [!NOTE]
    >  若要保留精靈的預設值，請略過此步驟。

1. 按一下 [完成] 以關閉精靈，並在開發環境中開啟新專案。

專案一旦建立完成之後，即可檢視在 [方案總管] 內建立的檔案。 如需精靈建立之專案檔案的詳細資訊，請參閱專案所產生的 ReadMe.txt 檔案。 如需檔案類型的詳細資訊，請參閱[為 Visual Studio C++ 專案建立的檔案類型](../../build/reference/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[屬性頁](../../build/reference/property-pages-visual-cpp.md)

