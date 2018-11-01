---
title: Windows FORMS-MFC 程式設計的差異
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: a284a74fe0b8cac0df43803951e3a5b5655f8189
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593176"
---
# <a name="windows-formsmfc-programming-differences"></a>Windows Form/MFC 程式設計的差異

中的主題[在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)描述 Windows Form 的 MFC 支援。 如果您不熟悉.NET Framework 或 MFC 程式設計，本主題會提供程式設計的差異，兩者之間的背景資訊。

Windows Form 是.NET Framework 上建立 Microsoft Windows 應用程式。 此架構提供現代、 物件導向、 可延伸的集合的類別，可讓您用來開發豐富的 Windows 應用程式。 使用 Windows Form，就可以建立豐富型用戶端應用程式，可以存取各種資料來源，並提供資料顯示和使用 Windows Form 控制項的資料編輯功能。

不過，如果您習慣使用 MFC 時，您可能用來建立特定類型的尚未明確地支援 Windows Form 中的應用程式。 Windows Forms 應用程式相當於 MFC 對話方塊應用程式。 不過，它們並不提供直接支援單一文件介面 (SDI)、 多重文件介面 (MDI)，其他如 OLE 文件伺服器/容器 ActiveX 文件、 文件/檢視支援的 MFC 應用程式類型的基礎結構和多個最上層介面 (MTI)。 您可以撰寫您自己的邏輯來建立這些應用程式。

如需有關 Windows Form 應用程式的詳細資訊，請參閱 < [Windows Form 簡介](/dotnet/framework/winforms/windows-forms-overview)。

顯示 Windows Form 搭配 MFC 使用的範例應用程式，請參閱[MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。

下列的 MFC 檢視或文件與路由功能的命令在 Windows Form 沒有對等項目：

- 殼層整合

   MFC 會處理文件上按一下滑鼠右鍵並選取這類動詞命令為開啟、 編輯或列印時，會使用殼層的命令列引數與動態資料交換 (DDE) 命令。 Windows Form 任何殼層整合並不會回應 shell 動詞命令。

- 文件範本

   在 MFC 中，文件範本會將包含在框架視窗 （在 MDI、 SDI 或 MTI 模式） 中，檢視與您所開啟的文件產生關聯。 Windows Form 有沒有相當於文件範本。

- 文件

   MFC 註冊文件檔案類型，並從殼層中開啟文件時處理的文件類型。 Windows Forms 的任何文件支援。

- 文件狀態

   MFC 會維護文件的變更狀態。 因此，當您關閉應用程式、 關閉的最後一個檢視，其中包含應用程式，或結束 Windows，MFC 會提示您儲存文件。 Windows Form 有沒有對等的支援。

- 命令

   MFC 會具有命令的概念。 功能表列、 工具列和快顯功能表所有可以叫用相同的命令，例如剪下和複製。 在 Windows Forms 中，命令會緊密繫結的事件，從特定的 UI 項目 （例如功能表項目）;因此，您必須明確地連結命令的所有事件。 您也可以處理多個事件與 Windows Form 中的單一處理常式。 如需詳細資訊，請參閱 <<c0> [ 連接至 Windows Forms 中的單一事件處理常式的多個事件](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms)。

- 命令路由

   MFC 命令路由，可讓現用檢視表或文件來處理命令。 因為相同的命令通常會有不同的意義不同的檢視 （例如，複製其行為與以不同的方式比在圖形編輯器中的文字編輯檢視中），命令必須由使用中的檢視。 Windows Form 功能表和工具列有沒有固有的了解使用中的檢視，因為您不能有不同的處理常式，如每種檢視類型您**MenuItem.Click**事件，而不需要撰寫額外的內部程式碼。

- 命令更新機制

   MFC 會具有更新機制的命令。 因此，在現用檢視表或文件是負責 UI 項目 （例如，啟用或停用功能表項目、 工具列按鈕和核取狀態） 的狀態。 Windows Form 有沒有對等的命令更新機制。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用 Windows Forms 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)
