---
title: 應用程式設定，MFC ActiveX 控制項精靈
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.appset
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
ms.openlocfilehash: 17d8ad581640611a5b517edd15609aa8052ecae4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677132"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>應用程式設定，MFC ActiveX 控制項精靈

您可使用 [MFC ActiveX 控制項精靈] 的這個頁面來設計基本功能並將其加入新的 MFC ActiveX 專案。 這些設定是套用至應用程式本身，而不是控制項的任何特定功能或項目。

- **執行階段授權**

   選取這個選項以產生要和控制項一起散發的使用者授權檔。 授權檔是文字檔，檔名為 *projname*.lic。 這個檔案必須位於與控制項之 DLL 相同的目錄中，如此才能在設計階段環境中建立控制項的執行個體。 您通常會將這個檔案和控制項一起散發，但您的客戶不會散發這個檔案。

- **產生說明檔**

   選取這個選項來產生截短的說明檔，並設定專案以包含控制項的說明。 如果預設專案建立時未選取這個選項，就只會產生在使用者以滑鼠右鍵按一下控制項、使用 F1 或按一下控制項容器上的 [說明]  時出現的 [關於]  方塊。

   > [!NOTE]
   > 說明的顯示方式取決於控制項與其容器的互動方式而定。 如果要將說明包含在容器內，就必須處理控制項和容器之間的訊息以適當顯示說明。

   當您使用精靈產生說明檔時，您的專案會包含下列項目：

   - .vcxproj 檔包含在專案建置時用來建置和設定說明檔的程式碼。

   - *projnamePropPage*.cpp 檔在建構函式中含有 [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) 函式。

   - projname.hpj 檔，這是說明編譯器用來建立 ActiveX 控制項說明檔的說明專案檔。 hpj 檔是文字檔，其中包含建置說明檔的資訊以及前往說明檔所含之其他檔案 (例如點陣圖) 的路徑。

   - 專案包含的 HLP 目錄內含專案說明點陣圖檔和說明主題檔 (*projname*.rtf)。 這個說明主題檔包含標準的說明主題，其適用於許多 ActiveX 控制項支援的通用屬性、事件及方法。 您可編輯 .rtf 檔來加入或移除特定說明主題。

## <a name="see-also"></a>另請參閱

[MFC ActiveX 控制項精靈](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控制項精靈、控制項名稱](../../mfc/reference/control-names-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控制項精靈、控制項設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)

