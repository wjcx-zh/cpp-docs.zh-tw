---
title: MFC 加入類別精靈、文件範本字串
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
ms.openlocfilehash: a5664a539af351051f9ae3642c089e51b54bc8cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662419"
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>MFC 加入類別精靈、文件範本字串

在精靈的此頁面是僅適用於類別符合下列準則：

- MFC 專案支援的文件/檢視架構。

- 新類別的基底類別[CFormView](../../mfc/reference/cformview-class.md)。

- 核取方塊**產生 DocTemplate 資源**會檢查**名稱**一節[MFC 類別精靈](../../mfc/reference/mfc-add-class-wizard.md)。

此精靈提供下列的值，以協助使用表單檢視的設計、 管理和當地語系化的預設值。 由於大部分的文件樣板字串可以看見並且由表單的使用者，他們會當地語系化成**資源語言**示[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 應用程式精靈頁面建立專案時。

> [!NOTE]
>  衍生類別的精靈不提供自動的列印支援`CFormView`。

請參閱[文件範本和文件/檢視建立流程](../../mfc/document-templates-and-the-document-view-creation-process.md)如需詳細資訊。

## <a name="nonlocalized-strings"></a>未當地語系化的字串

適用於建立使用者文件的應用程式。 使用者可以開啟和儲存文件更輕鬆地如果文件類型的副檔名和檔案類型識別碼。 因為由系統中，而不是由使用者使用，這些項目不會進行當地語系化。

- **副檔名**

   設定這個表單應用程式的文件類型相關聯的副檔名。 基礎類別名稱的檔案副檔名預設值。 例如，如果新的 MFC 類別命名為`CWidget`，根據預設，檔案的副檔名是。 wid 副檔名會在檔案篩選器和**開放**並**將儲存為**對話方塊。

   如果您變更副檔名時，變更會反映在**篩選器名稱** 方塊中。

   > [!NOTE]
   > 如果您變更預設的副檔名，不會包含句點。

- **檔案類型識別碼**

   在系統登錄中設定文件類型的標籤。

## <a name="localized-strings"></a>當地語系化的字串

產生的表單與讀取和使用應用程式的使用者，因此字串當地語系化的文件相關聯的字串。

- **文件類型名稱**

   識別應用程式的文件可以分組在其下的文件的類型。 根據預設，它根據類別的名稱。 例如，如果名為新的 MFC 類別**CWidget**，根據預設，文件類型名稱是小工具。 變更預設不會變更在此對話方塊中的任何其他選項。

- **篩選器名稱**

   設定使用者可指示以尋找指定的檔案類型的檔案名稱。 此選項可從**類型的檔案**並**存檔類型**標準的 Windows 中的選項**開啟**和**將儲存為**對話方塊。 根據預設，名稱根據專案名稱，再加上後面接著副檔名的檔案所示**副檔名**。 例如，如果您的專案命名為小工具，而檔案的副檔名為.wid，**篩選器名稱**預設為小工具檔案 (*.wid)。

- **檔案的新簡短名稱**

   設定名稱不會出現在標準 Windows**新增**對話方塊中，如果專案具有一個以上的文件範本。 如果您的應用程式[Automation 伺服程式](../../mfc/automation-servers.md)，此名稱做為您的 Automation 物件的簡短名稱。 根據預設，這個名稱根據類別名稱。

- **檔案類型完整名稱**

   設定系統登錄中的檔案類型名稱。 如果您的應用程式為 Automation 伺服程式，此名稱可為您的 Automation 物件的完整名稱。 根據預設，這個名稱根據類別名稱加上。文件。 例如，如果類別名稱是`CWidget`，則**檔案類型的長名稱**是小工具的文件。

- **文件類別**

   表示專案的文件類別。 根據預設，這個類別是主應用程式的文件類別，如下所示[檢閱產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)MFC 應用程式精靈頁面。 如果您在專案中新增其他文件類別，您可以從清單中，選取另一個文件類別。

## <a name="see-also"></a>另請參閱

[MFC 加入類別精靈](../../mfc/reference/mfc-add-class-wizard.md)<br/>
[MFC 類別](../../mfc/reference/adding-an-mfc-class.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)
