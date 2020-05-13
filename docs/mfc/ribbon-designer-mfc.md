---
title: 功能區設計工具 (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 8b66ff0f19392eb1685f8632a3fc4d9e90094304
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372793"
---
# <a name="ribbon-designer-mfc"></a>功能區設計工具 (MFC)

功能區設計工具可讓您建立和自訂 MFC 應用程式中的功能區。 功能區是可將命令組織成邏輯群組的使用者介面 (UI) 項目。 這些群組可出現在跨視窗頂端區域中的個別索引標籤上。 功能區取代了功能表列和工具列。 功能區可大幅改善應用程式可用性。 有關詳細資訊,請參閱[功能區](/windows/win32/uxguide/cmd-ribbons)。 下圖顯示功能區。

![MFC 功能區資源控制](../mfc/media/ribbon_no_callouts.png "MFC 功能區資源控制")

在早期版本的 Visual Studio 中,功能區必須透過編寫使用 MFC 功能區類(如[CMFCRibbonBar 類](../mfc/reference/cmfcribbonbar-class.md))的代碼來創建。 在 Visual Studio 2010 及更高版本中,功能區設計器提供了建構功能區的替代方法。 首先，建立及自訂功能區作為資源。 然後從 MFC 應用程式中的程式碼載入功能區資源。 您甚至可以一起使用功能區資源和 MFC 功能區類別。 例如，您可以建立功能區資源，然後使用程式碼在執行階段以程式設計方式將多個項目新增至其中。

## <a name="understanding-the-ribbon-designer"></a>了解功能區設計工具

功能區設計工具會建立功能區並將其儲存為資源。 當您建立功能區資源時，功能區設計工具會執行下列三項動作：

- 新增專案資源定義指令碼 (*.rc) 中的項目。 在下面的示例中,IDR_RIBBON是標識功能區資源的唯一名稱,RT_RIBBON_XML是資源類型,功能區.mfcribbon-ms 是資源檔的名稱。

```cpp
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- 將命令 ID 的定義新增至 resource.h。

```
#define IDR_RIBBON            307
```

- 建立功能區資源檔 (*.mfcribbon-ms)，其中包含定義功能區按鈕、控制項和屬性的 XML 程式碼。 功能區設計工具中的功能區變更會以 XML 格式儲存在資源檔中。 以下代碼範例顯示了 .mfcribbon-ms\*檔案的一部分內容:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

要在 MFC 應用程式中使用功能區資源,請通過調用[CMFC 功能區列::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource)來載入資源。

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>使用功能區設計工具建立功能區

下列兩個方法可將功能區資源新增至您的 MFC 專案中：

- 建立 MFC 應用程式並設定 MFC 專案精靈以建立功能區。 有關詳細資訊,請參閱[演練:使用 MFC 建立功能區應用程式](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)。

- 在現有的 MFC 專案中，建立功能區資源並將其載入。 有關詳細資訊,請參閱[演練:更新 MFC 塗鴉應用程式(第 1 部分)。](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)

如果您的專案已經以手動方式為功能區編碼，MFC 會具有函式，可用來將現有的功能區轉換為功能區資源。 有關詳細資訊,請參閱[如何:將現有 MFC 功能區轉換為功能區資源](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md)。

> [!NOTE]
> 在對話方塊架構應用程式中，無法建立功能區。 有關詳細資訊,請參閱[應用程式類型 MFC 應用程式精靈](../mfc/reference/application-type-mfc-application-wizard.md)。

## <a name="customizing-ribbons"></a>自訂功能區

若要在功能區設計工具中開啟功能區，請按兩下資源檢視中的功能區資源。 在設計工具中，您可以新增、移除及自訂功能區、應用程式按鈕或快速存取工具列上的項目。 您也可以將事件 (例如按一下按鈕事件和功能表事件) 連結到應用程式中的方法。

下圖顯示功能區設計工具中的不同元件。

![MFC 功能區設計工具](../mfc/media/ribbon_designer.png "MFC 功能區設計工具")

- **工具箱:** 包含可拖動到設計器曲面的控制項。

- **設計器表面:** 包含功能區資源的可視表示形式。

- **[類別精靈](reference/mfc-class-wizard.md):** 列出在設計器曲面上選擇的項的屬性。

- **資源檢視視窗:** 在項目中顯示包含功能區資源的資源。

- **功能區編輯器工具列:** 包含允許您預覽功能區並更改其可視主題的命令。

下列主題描述如何在功能區設計工具中使用這些功能。

- [如何：自訂應用程式按鈕](../mfc/how-to-customize-the-application-button.md)

- [如何：自訂快速存取工具列](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [如何：新增功能區控制項和事件處理常式](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [如何：從 MFC 應用程式載入功能區應用程式](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>功能區項目定義

![MFC 功能區](../mfc/media/ribbon.png "MFC 功能區")

- **應用程式按鈕:** 出現在功能區左上角的按鈕。 應用程式按鈕會取代 [檔案] 功能表，而且即使功能區最小化時也會出現。 按一下按鈕時，會顯示具有命令列表的功能表。

- **快速存取工具列:** 顯示常用命令的小型可自定義工具列。

- **類別**:表示功能區選項卡內容的邏輯分組。

- **類別預設按鈕:** 功能區最小化時出現在功能區上的按鈕。 按一下按鈕時，分類會以功能表的形式出現。

- **面板:** 功能區欄顯示一組相關控制件的區域。 每個功能區分類包含一或多個功能區面板。

- **功能區元素:** 面板中的控制項,例如按鈕和組合框。 要檢視可在功能區上管理的各種控制項,請參閱[功能區小工具範例:功能區小工具應用程式](../overview/visual-cpp-samples.md)。

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)<br/>
[使用資源檔](../windows/working-with-resource-files.md)
