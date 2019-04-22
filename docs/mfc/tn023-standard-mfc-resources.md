---
title: TN023:標準 MFC 資源
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.resources
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: d29f0ab2254a52e01f2016f64a37ddfce47955bb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780310"
---
# <a name="tn023-standard-mfc-resources"></a>TN023:標準 MFC 資源

這個附註說明 MFC 程式庫提供和需要的標準資源。

## <a name="standard-resources"></a>標準資源

MFC 提供兩種預先定義的資源類別，可讓您在應用程式中使用：美工圖案資源和標準架構資源。

美工圖案資源是與架構無關的額外資源，但您有可能會想要將它加入至您應用程式的使用者介面中。 下列美工圖案資源包含在 MFC 一般範例[美工圖案](../overview/visual-cpp-samples.md):

- Common.rc:單一檔案的資源，其中包含：

   - 表示各種商務和資料處理工作圖示的大型集合。

   - 許多常見的游標 (請參閱 Afxres.rc)。

   - 包含數個工具列按鈕的工具列點陣圖。

   - Commdlg.dll 使用的點陣圖和圖示資源。

- Indicate.rc:包含狀態列索引鍵狀態指標，例如 Caps lock 的 「 上限 」 的字串資源。

- Prompts.rc:ID_FILE_NEW 包含每個預先定義的命令，例如 [建立新的文件] 的功能表提示字串資源。

- Commdlg.rc:視覺效果C++相容.rc 檔案，其中包含標準 COMMDLG 對話方塊範本。

標準架構資源為架構依存於內部實作，具有 AFX 定義之 ID 的資源。 您很少需要變更這些 AFX 定義的資源。 如果要進行變更，您應該遵循本主題稍後概述的程序進行。

下列架構資源位於 MFC\INCLUDE 目錄中：

- Afxres.rc:Framework 所使用的通用資源。

- Afxprint.rc:列印與資源。

- Afxolecl.rc:與 OLE 用戶端應用程式的資源。

- Afxolev.rc:與完整 OLE 伺服器應用程式的資源。

## <a name="using-clip-art-resources"></a>使用美工圖案資源

#### <a name="to-use-a-clip-art-binary-resource"></a>使用美工圖案二進位資源

1. 在 Visual C++ 中開啟應用程式的資源檔。

1. 開啟 Common.rc。 這個檔案包含所有二進位美工圖案資源。 因為 Common.rc 檔案需要進行編譯，因此可能需要一些時間。

1. 當您要從 Common.rc 拖曳想要使用的資源到您應用程式的資源檔時，請按住 CTRL 鍵。

若要使用其他美工圖案資源，請遵循相同的步驟進行。 唯一的差異在於您會開啟適當的 .rc 檔而不是 Common.rc。

> [!NOTE]
>  請小心不要在無意中將資源移動至 Common.rc 的外面。 如果您在按住 CTRL 鍵的同時拖曳資源，則會建立複本。 如果您在拖曳時沒有按住 CTRL 鍵，則會移動資源。 如果擔心您會不小心變更 Common.rc 檔案，請在詢問您是否儲存 Common.rc 的變更時按一下 [否]。

> [!NOTE]
>  .Rc 資源檔中，可避免您不小心儲存在標準.rc 檔上有特殊 TEXTINCLUDE 資源。

### <a name="customizing-standard-framework-resources"></a>自訂標準架構資源

在應用程式的資源檔中使用 #include 命令，通常可將標準架構資源包含到應用程式中。 AppWizard 將會產生一個資源檔。 這個檔案包含適當的標準架構資源，視您選取的 AppWizard 選項而定。 藉由變更編譯時期指示詞，您可以檢閱、加入或移除已包含的資源。 若要這樣做，請開啟**Resource**功能表，然後選取**Set Includes**。 請參閱「編譯時期指示詞」編輯項目。 例如: 

```
#include "afxres.rc"
#include "afxprint.rc"
```

最常見的自訂標準架構資源案例為加入或移除額外的列印、OLE 用戶端和 OLE 伺服器支援。

在某些較罕見的情況下，您可能會想要為您的特定應用程式自訂標準架構資源的內容，而不只是加入和刪除整個檔案。 下列步驟顯示如何限制包含的資源：

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>自訂標準資源檔的內容

1. 在 Visual C++ 中開啟資源檔。

1. 使用 [Resource Set Includes] 命令，移除您要自訂之標準 .rc 檔的 `#include`。 例如，若要自訂列印預覽工具列，請移除 `#include "afxprint.rc"` 這一行。

1. 開啟 MFC\INCLUDE 中適當的標準資源檔。 根據本主題稍早的範例，其適當的檔案為 MFC\Include\Aafxprint.rc

1. 從標準 .rc 檔複製所有資源至您的應用程式資源檔案。

1. 在您的應用程式資源檔中修改標準資源的複本。

> [!NOTE]
>  請勿直接在標準 .rc 檔中修改資源。 這麼做會修改每個應用程式中可用的資源，而不只是目前應用程式中可用的資源。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
