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
ms.openlocfilehash: ea80b67b3f6bb6980e4e8f7f12a967cb7bb5b6c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218725"
---
# <a name="print-preview-architecture"></a>預覽列印架構

本文說明 MFC 架構如何實作預覽列印功能。 涵蓋的主題包括：

- [預覽列印流程](#_core_the_print_preview_process)

- [修改預覽列印](#_core_modifying_print_preview)

預覽列印與螢幕顯示和列印稍有不同，因為應用程式必須使用螢幕模擬印表機，而不是直接在裝置上繪製影像。 要做到這一點，Microsoft Foundation Class Library 會定義衍生自特殊 （未記載） 類別[CDC 類別](../mfc/reference/cdc-class.md)稱為`CPreviewDC`。 所有 `CDC` 物件都包含兩種裝置內容，不過兩者通常相同。 在 `CPreviewDC`物件，它們是不同： 第一個代表要模擬的印表機，而第二個代表實際顯示輸出的螢幕。

##  <a name="_core_the_print_preview_process"></a> 預覽列印流程

當使用者選取從 預覽列印 命令**檔案** 功能表中，此架構會建立`CPreviewDC`物件。 當您的應用程式執行設定印表機裝置內容之特性的作業時，架構也會在螢幕裝置內容上執行類似的作業。 例如，如果您的應用程式選取了列印字型，則架構也會選取模擬印表機字型的螢幕顯示字型。 只要您的應用程式將輸出傳送至印表機，架構就會將輸出傳送至螢幕。

預覽列印與列印繪製文件頁面的順序也各不相同。 在列印期間，架構會繼續執行列印迴圈，直到完成呈現特定頁面範圍為止。 在預覽列印期間一次會顯示一頁或兩頁，然後應用程式便會等待；在使用者回應之前，不會再顯示其他頁面。 列印在預覽期間，應用程式也必須回應 WM_PAINT 訊息時，就如同正常螢幕顯示。

[CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)呼叫函式會叫用預覽模式時，就像它是在列印工作的開頭。 [CPrintInfo 結構](../mfc/reference/cprintinfo-structure.md)傳遞至函數的結構包含數個成員來調整預覽列印作業的某些特性，您可以設定其值。 例如，您可以設定*m_nNumPreviewPages*來指定您是否想要預覽文件在一頁或兩頁模式中的成員。

##  <a name="_core_modifying_print_preview"></a> 修改預覽列印

您可以輕鬆透過數種不同的方式修改預覽列印的行為和外觀。 例如，這當中包括可以：

- 讓預覽列印視窗顯示捲軸，方便您存取文件的任何頁面。

- 讓預覽列印從目前頁面開始顯示，藉此維持文件中使用者的位置。

- 對預覽列印和列印執行不同的初始化。

- 讓預覽列印以您自訂的格式顯示頁碼。

如果您知道文件的長度，並且以適當的值呼叫 `SetMaxPage`，架構就能夠在預覽模式中以及列印期間使用這項資訊。 一旦架構得知文件的長度，就能夠在預覽視窗中提供捲軸，讓使用者在預覽模式中上下捲動文件。 如果您尚未設定文件的長度，架構就無法定位捲動方塊以指出目前位置，因此架構就不會加入捲軸。 在這種情況下，使用者必須使用預覽視窗的控制列上的 [下一頁] 和 [上一頁] 按鈕瀏覽文件的頁面。

預覽列印，您可能會有用來指派值給*m_nCurPage*隸屬`CPrintInfo`，即使您不會這麼一般列印。 在一般列印期間，這個成員會將架構中的資訊帶至檢視類別。 架構就是透過這種方式告知檢視要列印的頁面。

相反地，當預覽列印模式啟動時， *m_nCurPage*成員帶有在相反方向的資訊： 從架構檢視。 架構會使用這個成員的值判斷應該先預覽哪個頁面。 這個成員的預設值為 1，因此文件的第一頁會最先顯示。 您可以覆寫 `OnPreparePrinting`，將這個成員設定為叫用 [預覽列印] 命令時要檢視的頁碼。 如此一來，從一般顯示模式轉換到預覽列印模式時，應用程式就會維持使用者的目前位置。

有時您會希望 `OnPreparePrinting` 依據呼叫執行的工作為列印或是預覽列印，執行不同的初始化作業。 您可以檢查來判斷這*m_bPreview*中的成員變數`CPrintInfo`結構。 這個成員設定為 **，則為 TRUE**叫用預覽列印時。

`CPrintInfo`結構也包含名為成員*m_strPageDesc*，這用來格式化單頁和多頁模式中螢幕的底部顯示的字串。 這些字串是表單的預設 「 頁面*n*"和"頁面*n* - *m*，「 但您可以修改*m_strPageDesc*從內`OnPreparePrinting`並將字串設定為更詳細的說明。 請參閱[CPrintInfo 結構](../mfc/reference/cprintinfo-structure.md)中*MFC 參考 》* 如需詳細資訊。

## <a name="see-also"></a>另請參閱

[列印和預覽列印](../mfc/printing-and-print-preview.md)<br/>
[列印](../mfc/printing.md)<br/>
[CView 類別](../mfc/reference/cview-class.md)<br/>
[CDC 類別](../mfc/reference/cdc-class.md)
