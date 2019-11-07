---
title: Windows Forms MFC 程式設計差異
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 52de36217a5ab47eddcbe1abd6617860dcb910b8
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73704179"
---
# <a name="windows-formsmfc-programming-differences"></a>Windows Form/MFC 程式設計的差異

在 MFC 中[使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)中的主題會描述 WINDOWS FORMS 的 MFC 支援。 如果您不熟悉 .NET Framework 或 MFC 程式設計，本主題會提供兩者之間的程式設計差異的背景資訊。

Windows Forms 是用來在 .NET Framework 上建立 Microsoft Windows 應用程式。 此架構提供了一組現代化、物件導向、可擴充的類別，可讓您開發豐富的 Windows 應用程式。 使用 Windows Forms，您可以建立豐富的用戶端應用程式，以存取各種不同的資料來源，並使用 Windows Forms 控制項來提供資料顯示和資料編輯工具。

不過，如果您習慣使用 MFC，您可能會用來建立 Windows Forms 中尚未明確支援的特定類型應用程式。 Windows Forms 的應用程式相當於 MFC 對話應用程式。 不過，它們不會提供直接支援其他 MFC 應用程式類型的基礎結構，例如 OLE 檔案伺服器/容器、ActiveX 檔、單一檔介面（SDI）的檔/視圖支援、多重文件介面（MDI），以及多個頂層介面（MTI）。 您可以撰寫自己的邏輯來建立這些應用程式。

如需 Windows Forms 應用程式的詳細資訊，請參閱[Windows Forms 簡介](/dotnet/framework/winforms/windows-forms-overview)。

如需顯示與 MFC 搭配使用之 Windows Forms 的範例應用程式，請參閱[mfc 和 Windows Forms 整合](https://www.microsoft.com/en-us/download/details.aspx?id=2113)。

下列 MFC 視圖或檔和命令路由功能在 Windows Forms 中沒有對等專案：

- Shell 整合

   當您以滑鼠右鍵按一下檔，然後選取 [開啟]、[編輯] 或 [列印] 這類動詞時，MFC 會處理 shell 使用的動態資料交換（DDE）命令和命令列引數。 Windows Forms 沒有 shell 整合，而且不會回應 shell 動詞命令。

- 檔範本

   在 MFC 中，檔範本會將包含在框架視窗（在 MDI、SDI 或 MTI 模式中）的視圖與您開啟的檔產生關聯。 Windows Forms 不等於檔範本。

- 文件

   MFC 會在從 shell 開啟檔時，註冊檔檔類型並處理檔案類型。 Windows Forms 沒有檔支援。

- 檔狀態

   MFC 會維護檔的已變更狀態。 因此，當您關閉應用程式時，請關閉包含應用程式的最後一個視圖，或從 Windows 結束，MFC 會提示您儲存檔。 Windows Forms 沒有對等的支援。

- 命令

   MFC 具有命令的概念。 功能表列、工具列和內容功能表都可以叫用相同的命令，例如，剪下和複製。 在 Windows Forms 中，命令會從特定的 UI 元素（例如功能表項目）緊密系結事件;因此，您必須明確地連結所有命令事件。 您也可以在 Windows Forms 中使用單一處理程式來處理多個事件。 如需詳細資訊，請參閱[在 Windows Forms 中將多個事件連接到單一事件處理常式](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms)。

- 命令路由

   MFC 命令路由可讓使用中的 view 或 document 來處理命令。 因為相同的命令通常對於不同的視圖具有不同的意義（例如，複製在文字編輯檢視中的行為不同于圖形編輯器），所以必須由現用視圖來處理命令。 因為 Windows Forms 功能表和工具列並不會對使用中的視圖有任何固有的瞭解，所以您的 MenuItem 的每個檢視類型不能有不同的處理常式 **。請按一下**[事件]，而不需要撰寫額外的內部

- 命令更新機制

   MFC 有一個命令更新機制。 因此，即時檢視或檔會負責 UI 元素的狀態（例如，啟用或停用功能表項目或工具按鈕，以及已核取的狀態）。 Windows Forms 沒有對等的命令更新機制。

## <a name="see-also"></a>請參閱

[在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)
