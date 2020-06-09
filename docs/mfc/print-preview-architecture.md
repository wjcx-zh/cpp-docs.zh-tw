---
title: 預覽列印架構
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 1956313d4e904255ba59e79690fe3d7144669a29
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623943"
---
# <a name="print-preview-architecture"></a>預覽列印架構

本文說明 MFC 架構如何實作預覽列印功能。 涵蓋的主題包括：

- [預覽列印流程](#_core_the_print_preview_process)

- [修改預覽列印](#_core_modifying_print_preview)

預覽列印與螢幕顯示和列印稍有不同，因為應用程式必須使用螢幕模擬印表機，而不是直接在裝置上繪製影像。 為了配合此，MFC 程式庫定義了衍生自[CDC 類別](reference/cdc-class.md)的特殊（未記載）類別，名為 `CPreviewDC` 。 所有 `CDC` 物件都包含兩種裝置內容，不過兩者通常相同。 在 `CPreviewDC` 物件中，它們是不同的：第一個代表正在模擬的印表機，第二個則代表實際顯示輸出的螢幕。

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>預覽列印流程

當使用者**從 [檔案**] 功能表選取 [預覽列印] 命令時，架構會建立 `CPreviewDC` 物件。 當您的應用程式執行設定印表機裝置內容之特性的作業時，架構也會在螢幕裝置內容上執行類似的作業。 例如，如果您的應用程式選取了列印字型，則架構也會選取模擬印表機字型的螢幕顯示字型。 只要您的應用程式將輸出傳送至印表機，架構就會將輸出傳送至螢幕。

預覽列印與列印繪製文件頁面的順序也各不相同。 在列印期間，架構會繼續執行列印迴圈，直到完成呈現特定頁面範圍為止。 在預覽列印期間一次會顯示一頁或兩頁，然後應用程式便會等待；在使用者回應之前，不會再顯示其他頁面。 在預覽列印期間，應用程式也必須回應 WM_PAINT 訊息，就像在一般螢幕顯示期間一樣。

叫用預覽模式時，會呼叫[CView：： OnPreparePrinting](reference/cview-class.md#onprepareprinting)函式，就像在列印工作開始時一樣。 傳遞至函式的[CPrintInfo 結構](reference/cprintinfo-structure.md)結構包含數個成員，您可以設定其值來調整預覽列印作業的特定特性。 例如，您可以設定*m_nNumPreviewPages*成員，以指定是否要以一頁或兩頁模式來預覽檔。

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>修改預覽列印

您可以輕鬆透過數種不同的方式修改預覽列印的行為和外觀。 例如，這當中包括可以：

- 讓預覽列印視窗顯示捲軸，方便您存取文件的任何頁面。

- 讓預覽列印從目前頁面開始顯示，藉此維持文件中使用者的位置。

- 對預覽列印和列印執行不同的初始化。

- 讓預覽列印以您自訂的格式顯示頁碼。

如果您知道文件的長度，並且以適當的值呼叫 `SetMaxPage`，架構就能夠在預覽模式中以及列印期間使用這項資訊。 一旦架構得知文件的長度，就能夠在預覽視窗中提供捲軸，讓使用者在預覽模式中上下捲動文件。 如果您尚未設定文件的長度，架構就無法定位捲動方塊以指出目前位置，因此架構就不會加入捲軸。 在這種情況下，使用者必須使用預覽視窗的控制列上的 [下一頁] 和 [上一頁] 按鈕瀏覽文件的頁面。

針對 [預覽列印]，將值指派給的*m_nCurPage*成員可能會很有用 `CPrintInfo` ，即使您永遠不會進行一般列印也一樣。 在一般列印期間，這個成員會將架構中的資訊帶至檢視類別。 架構就是透過這種方式告知檢視要列印的頁面。

相反地，當「預覽列印」模式啟動時， *m_nCurPage*成員會以相反的方向來攜帶資訊：從視圖到架構。 架構會使用這個成員的值判斷應該先預覽哪個頁面。 這個成員的預設值為 1，因此文件的第一頁會最先顯示。 您可以覆寫 `OnPreparePrinting`，將這個成員設定為叫用 [預覽列印] 命令時要檢視的頁碼。 如此一來，從一般顯示模式轉換到預覽列印模式時，應用程式就會維持使用者的目前位置。

有時您會希望 `OnPreparePrinting` 依據呼叫執行的工作為列印或是預覽列印，執行不同的初始化作業。 您可以藉由檢查結構中的*m_bPreview*成員變數來判斷這一點 `CPrintInfo` 。 當叫用預覽列印時，這個成員會設定為**TRUE** 。

`CPrintInfo`結構也包含名為*m_strPageDesc*的成員，用來格式化單頁和多頁模式中顯示在畫面底部的字串。 根據預設，這些字串的格式為 "Page *n*" 和 "Pages *n*  -  *m*"，但您可以從*m_strPageDesc*內修改 m_strPageDesc `OnPreparePrinting` ，並將字串設定為更詳盡的內容。 如需詳細資訊，請參閱*MFC 參考*中的[CPrintInfo 結構](reference/cprintinfo-structure.md)。

## <a name="see-also"></a>另請參閱

[列印和預覽列印](printing-and-print-preview.md)<br/>
[列印](printing.md)<br/>
[CView 類別](reference/cview-class.md)<br/>
[CDC 類別](reference/cdc-class.md)
