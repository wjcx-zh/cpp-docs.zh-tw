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
ms.openlocfilehash: 5943edc22cd48ed10d152f72624467ff87104b96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375951"
---
# <a name="print-preview-architecture"></a>預覽列印架構

本文說明 MFC 架構如何實作預覽列印功能。 涵蓋的主題包括：

- [預覽列印流程](#_core_the_print_preview_process)

- [變更列印預覽](#_core_modifying_print_preview)

預覽列印與螢幕顯示和列印稍有不同，因為應用程式必須使用螢幕模擬印表機，而不是直接在裝置上繪製影像。 為了適應這種情況,Microsoft 基礎類別庫定義了派生自[CDC 類別](../mfc/reference/cdc-class.md)的特殊(未記錄`CPreviewDC`)類別, 稱為 。 所有 `CDC` 物件都包含兩種裝置內容，不過兩者通常相同。 在物件`CPreviewDC`中,它們是不同的:第一個表示正在模擬的印表機,第二個表示實際顯示輸出的螢幕。

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>預覽程序

當使用者從「**檔案**」功能表中選擇「列印預覽」命令時,框架將創建一`CPreviewDC`個物件。 當您的應用程式執行設定印表機裝置內容之特性的作業時，架構也會在螢幕裝置內容上執行類似的作業。 例如，如果您的應用程式選取了列印字型，則架構也會選取模擬印表機字型的螢幕顯示字型。 只要您的應用程式將輸出傳送至印表機，架構就會將輸出傳送至螢幕。

預覽列印與列印繪製文件頁面的順序也各不相同。 在列印期間，架構會繼續執行列印迴圈，直到完成呈現特定頁面範圍為止。 在預覽列印期間一次會顯示一頁或兩頁，然後應用程式便會等待；在使用者回應之前，不會再顯示其他頁面。 在列印預覽期間,應用程式還必須回應WM_PAINT消息,就像在普通螢幕顯示時一樣。

調用預覽模式時調用[CView:onPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)功能,就像列印作業開始時一樣。 傳遞給該函數的[CPrintInfo 結構](../mfc/reference/cprintinfo-structure.md)包含多個成員,您可以設置其值以調整列印預覽操作的某些特徵。 例如,您可以將*m_nNumPreviewPages*成員設置為指定是要以單頁還是兩頁模式預覽文檔。

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>變更列印預覽

您可以輕鬆透過數種不同的方式修改預覽列印的行為和外觀。 例如，這當中包括可以：

- 讓預覽列印視窗顯示捲軸，方便您存取文件的任何頁面。

- 讓預覽列印從目前頁面開始顯示，藉此維持文件中使用者的位置。

- 對預覽列印和列印執行不同的初始化。

- 讓預覽列印以您自訂的格式顯示頁碼。

如果您知道文件的長度，並且以適當的值呼叫 `SetMaxPage`，架構就能夠在預覽模式中以及列印期間使用這項資訊。 一旦架構得知文件的長度，就能夠在預覽視窗中提供捲軸，讓使用者在預覽模式中上下捲動文件。 如果您尚未設定文件的長度，架構就無法定位捲動方塊以指出目前位置，因此架構就不會加入捲軸。 在這種情況下，使用者必須使用預覽視窗的控制列上的 [下一頁] 和 [上一頁] 按鈕瀏覽文件的頁面。

對於列印預覽,您可能會發現將值分配給m_nCurPage`CPrintInfo`*成員很有用*,即使您永遠不會為普通列印分配該值。 在一般列印期間，這個成員會將架構中的資訊帶至檢視類別。 架構就是透過這種方式告知檢視要列印的頁面。

相反,當開始列印預覽模式時 *,m_nCurPage*成員以相反的方向傳遞資訊:從視圖到框架。 架構會使用這個成員的值判斷應該先預覽哪個頁面。 這個成員的預設值為 1，因此文件的第一頁會最先顯示。 您可以覆寫 `OnPreparePrinting`，將這個成員設定為叫用 [預覽列印] 命令時要檢視的頁碼。 如此一來，從一般顯示模式轉換到預覽列印模式時，應用程式就會維持使用者的目前位置。

有時您會希望 `OnPreparePrinting` 依據呼叫執行的工作為列印或是預覽列印，執行不同的初始化作業。 您可以通過檢查結構中*m_bPreview*成員變數來確定`CPrintInfo`這一點。 呼叫列印預覽時,此成員設置為**TRUE。**

該`CPrintInfo`結構還包含名為*m_strPageDesc*的成員,該成員用於以單頁和多頁模式設置螢幕底部顯示的字串的格式。 預設情況下,這些字串的形式是「頁*n」* 和「頁*n* - *m」,* 但可以從*m_strPageDesc*內部`OnPreparePrinting`修改m_strPageDesc並將字串設置為更詳細的東西。 有關詳細資訊,請參閱*MFC 參考*中的[CPrintInfo 結構](../mfc/reference/cprintinfo-structure.md)。

## <a name="see-also"></a>另請參閱

[列印和預覽列印](../mfc/printing-and-print-preview.md)<br/>
[列印](../mfc/printing.md)<br/>
[CView 類別](../mfc/reference/cview-class.md)<br/>
[CDC 類別](../mfc/reference/cdc-class.md)
