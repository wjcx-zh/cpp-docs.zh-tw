---
title: TN031：控制列
ms.date: 11/04/2016
f1_keywords:
- vc.controls.bars
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
ms.openlocfilehash: 37c3a15c281018260e65508dee3799ab0011dbfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370298"
---
# <a name="tn031-control-bars"></a>TN031：控制列

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

這個說明描述了 MFC 中的控制`CDockBar`欄位 :一般 CControlBar、CStatusBar、CToolbar、CDialogBar 和 。 [CControlBar](#_mfcnotes_ccontrolbar) [CStatusBar](#_mfcnotes_cstatusbar) [CToolBar](#_mfcnotes_ctoolbar) [CDialogBar](#_mfcnotes_cdialogbar)

## <a name="ccontrolbar"></a><a name="_mfcnotes_ccontrolbar"></a> CControlBar

A`ControlBar``CWnd`是 派生類,用於:

- 對齊框架視窗的頂端或底部。

- 可能包含作為 HWND 型控制項 (例如 `CDialogBar`) 或非`HWND` 型項目 (例如 `CToolBar`、 `CStatusBar`) 的子項目。

控制列支援其他樣式︰

- CBRS_TOP(預設值)將控制欄固定到頂部。

- CBRS_BOTTOM將控制桿固定到底部。

- CBRS_NOALIGN當父控件調整大小時,請勿重新置放控制欄。

衍生自 `CControlBar` 的類別提供更有趣的實作︰

- `CStatusBar` 狀態列，項目是含有文字的狀態列窗格。

- `CToolBar` 工具列，項目是對齊成一列的點陣圖按鈕。

- `CDialogBar` 類似工具列的框架，其中包含標準 Windows 控制項 (從對話方塊範本資源建立)。

- `CDockBar`其他`CControlBar`派生物件的通用停靠區域。 此類別中可用的特定成員函式和變數在未來版本中可能會有所變更。

所有控制列物件/視窗都是某些父框架視窗的子視窗。 它們通常會加入框架 (例如 MDI 用戶端或檢視) 的工作區成為同層級。 控制列的子視窗識別碼很重要。 控制列的預設配置僅適用於其識別碼在 AFX_IDW_CONTROLBAR_FIRST 到 AFX_IDW_CONTROLBAR_LAST 範圍內的控制列。 請注意，即使有 256 個控制列識別碼的範圍，前 32 個控制列識別碼由於受到預覽列印架構直接支援，因此是特殊的。

`CControlBar` 類別為下列項目提供標準實作︰

- 將控制列對齊框架頂端、底部或任一側。

- 配置控制項目陣列。

- 支援衍生類別的實作。

C++ 控制列物件通常會內嵌為 `CFrameWnd` 衍生類別的成員，而且會在終結父 `HWND` 和物件時遭到清除。 如果您需要將控制列物件配置到堆積上，您可以直接將 *m_bAutoDestruct* 成員設定為 **TRUE** ，讓控制列在終結**時「** 刪除此物件 `HWND` 」。

> [!NOTE]
> 如果`CControlBar`創建自己的派生類,而不是使用 MFC 的派生類之`CStatusBar`一`CToolBar`,`CDialogBar`例如 , 或, 則需要設置*m_dwStyle*數據成員。 這可以在重寫 中`Create`完成 :

```
// CMyControlBar is derived from CControlBar
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)
{
    m_dwStyle = dwStyle;

.
.
.
}
```

**控制列配置演算法**

控制列配置演算法很簡單。 框架視窗會將訊息 WM_SIZEPARENT 傳送至控制列範圍內的所有子系。 父代工作區矩形的指標會連同此訊息一起傳遞。 此訊息會依 Z 軸順序傳送至子系。 控制列子系使用這項資訊自我放置，以及減少父代工作區的大小。 最後留給一般工作區的矩形 (較小的控制列) 是用來放置主用戶端視窗 (通常是 MDI 用戶端、檢視或分隔視窗)。

如需詳細資訊，請參閱 `CWnd::RepositionBars` 和 `CFrameWnd::RecalcLayout` 。

MFC 專用 Windows 消息(包括WM_SIZEPARENT)記錄在[技術說明 24](../mfc/tn024-mfc-defined-messages-and-resources.md)中。

## <a name="cstatusbar"></a><a name="_mfcnotes_cstatusbar"></a>CStatusbar

狀態列是具有一列文字輸出窗格的控制列。 文字輸出窗格有兩種常見的用法：

- 作為訊息列

     (例如標準功能表說明訊息列)。 通常會透過以 0 起始的索引來存取。

- 如同狀態指標

     (例如 CAP、NUM 和 SCRL 指標)。 通常會透過字串/命令 ID 來存取。

狀態列的字型是 10 點 MS Sans Serif (依照《Windows 介面應用程式設計指南》所指定，或 10 點瑞士調和間距字型的字型對應程式最符合項目)。 在特定版本的 Windows 上 (例如日文版)，選取的字型會不同。

狀態列中使用的色彩也會與《Windows 介面應用程式設計指南》的建議一致。 這些色彩未經過硬式編碼，而且會動態變更以便回應使用者在 [控制台] 中的自訂。

|Item|Windows 色彩值|預設 RGB|
|----------|-------------------------|-----------------|
|狀態列背景|COLOR_BTNFACE|RGB(192, 192, 192)|
|狀態列文字|COLOR_BTNTEXT|RGB(000, 000, 000)|
|狀態列上/左邊緣|COLOR_BTNHIGHLIGHT|RGB(255, 255, 255)|
|狀態列下/右邊緣|COLOR_BTNSHADOW|RGB(128, 128, 128)|

**CStatusBar 的 CCmdUI 支援**

指標通常更新的方式是通過ON_UPDATE_COMMAND_UI機制。 在空閒時間,狀態列將調用帶有指示器窗格的字串 ID 的ON_UPDATE_COMMAND_UI處理程式。

ON_UPDATE_COMMAND_UI處理程式可以呼叫:

- `Enable`:啟用或禁用窗格。 停用的窗格看起來與啟用的窗格完全相同，但會隱藏文字 (亦即關閉文字指標)。

- `SetText`:更改文字。 如果使用此選項，請務必小心，因為窗格不會自動調整大小。

如需 [建立和自訂 API 的詳細資訊，請參閱＜類別庫參考＞](../mfc/reference/cstatusbar-class.md)*中的* CStatusBar `CStatusBar` 類別。 狀態列的大部分自訂應該在初始顯示狀態列之前完成。

狀態列只支援一個壓縮窗格，通常是第一個窗格。 該窗格的大小其實是大小下限。 如果狀態列大於所有窗格的大小下限，任何額外的寬度都會指定給此壓縮窗格。 具有狀態列的預設應用程式，由於其第一個窗格已壓縮，因此 CAP、NUM 和 SCRL 指標會靠右對齊。

## <a name="ctoolbar"></a><a name="_mfcnotes_ctoolbar"></a>CToolBar

工具列是具有一列點陣圖按鈕 (可能包含分隔符號) 的控制列。 支援兩種按鈕樣式︰按鈕和核取方塊按鈕。 可以使用複選框按鈕構建無線電組功能,並ON_UPDATE_COMMAND_UI。

工具列中的所有點陣圖按鈕都是取自一個點陣圖。 此點陣圖必須包含每個按鈕的一個圖像或字符。 一般而言，點陣圖中的圖像/字符順序與在螢幕上繪製的順序相同 (您可以使用自訂 API 對此進行變更)。

每個按鈕的大小必須相同。 預設為標準 24x22 像素。 每個圖像/字符的大小必須相同，而且必須並排顯示於點陣圖中。 預設圖像/字符大小為 16x15 像素。 因此，若是具有 10 個按鈕的工具列 (使用標準大小)，您需要寬 160 像素、高 15 像素的點陣圖。

每個按鈕只能有一個圖像/字符。 該唯一的圖像/字符會利用演算法產生不同的按鈕狀態和樣式 (例如按下、向上、向下、停用、停用向下、不定)。 理論上可以使用任何色彩的點陣圖或 DIB。 用於產生不同按鈕狀態的演算法在原始圖像是灰階時的成效最佳。 如需範例，請參閱 MFC 一般範例 [美工圖案](../overview/visual-cpp-samples.md) 中所提供的標準工具列按鈕和工具列按鈕美工圖案。

工具列中使用的色彩也會與《Windows 介面應用程式設計指南》的建議一致。 這些色彩未經過硬式編碼，而且會動態變更以便回應使用者在 [控制台] 中的自訂。

|Item|Windows 色彩值|預設 RGB|
|----------|-------------------------|-----------------|
|工具列背景|COLOR_BTNFACE|RGB(192,192,192)|
|工具列按鈕上/左邊緣|COLOR_BTNHIGHLIGHT|RGB(255,255,255)|
|工具列按鈕下/右邊緣|COLOR_BTNSHADOW|RGB(128,128,128)|

此外，工具列點陣圖按鈕會重新著色，就像標準 Windows 按鈕控制項一樣。 當點陣圖從資源載入而需要回應系統色彩變更時，就會進行此重新著色，以便回應使用者在 [控制台] 中的自訂。 工具列點陣圖中的下列色彩會自動重新著色，因此應該謹慎使用。 如果您不想讓點陣圖的某部分重新著色，請使用最接近對應 RGB 值的色彩。 此對應是以實際 RGB 值為準。

|RGB 值|動態對應的色彩值|
|---------------|------------------------------------|
|RGB(000, 000, 000)|COLOR_BTNTEXT|
|RGB(128, 128, 128)|COLOR_BTNSHADOW|
|RGB(192, 192, 192)|COLOR_BTNFACE|
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|

如需 [建立和自訂 API 的詳細資訊，請參閱＜類別庫參考＞](../mfc/reference/ctoolbar-class.md)*中的* CToolBar `CToolBar` 類別。 工具列的大部分自訂應該在初始顯示工具列之前完成。

自訂 API 可用來調整按鈕 ID、樣式、空格字元寬度，以及按鈕所使用的圖像/字符。 根據預設，您不需要使用這些 API。

## <a name="ccmdui-support-for-ctoolbar"></a>CToolBar 的 CCmdUI 支援

工具欄按鈕始終更新的方式是通過ON_UPDATE_COMMAND_UI機制。 在空閒時間,工具列將調用帶有該按鈕的命令 ID 的ON_UPDATE_COMMAND_UI處理程式。 ON_UPDATE_COMMAND_UI不調用分隔符,但稱為按鈕和複選框按鈕。

ON_UPDATE_COMMAND_UI處理程式可以呼叫:

- `Enable`:啟用或禁用按鈕。 這對按鈕和核取方塊按鈕的作用相同。

- `SetCheck`：若要設定按鈕的選取狀態。 為工具列按鈕呼叫此選項會將其轉換成核取方塊按鈕。 `SetCheck` 接受參數為 0 (未選取)、1 (已選取) 或 2 (不定)

- `SetRadio`︰ `SetCheck`的速記。

核取方塊按鈕是「自動」核取方塊按鈕；也就是說，當使用者按下按鈕時，這些按鈕會立即變更狀態。 「已選取」是向下或壓下的狀態。 沒有內建使用者介面方法可將按鈕變更為「不定」狀態，您必須透過程式碼來完成。

自定義 API 將允許您更改給定工具列按鈕的狀態,最好在工具列按鈕表示的命令ON_UPDATE_COMMAND_UI處理程式中更改這些狀態。 請記住,空閒處理將更改工具列按鈕的狀態與ON_UPDATE_COMMAND_UI處理程式,因此,通過 SetButtonStyle 對這些狀態所做的任何更改可能會在下一個空閒後丟失。

工具列按鈕將發送WM_COMMAND消息(如普通按鈕或功能表項),通常由提供ON_UPDATE_COMMAND_UI處理程式的同一類中的ON_COMMAND處理程序處理。

用於顯示狀態的工具列按鈕樣式 (TBBS_ 值) 有四種︰

- TBBS_CHECKED：核取方塊目前為按下 (向下)。

- TBBS_INDETERMINATE：核取方塊目前為不定。

- TBBS_DISABLED：按鈕目前為停用。

- TBBS_PRESSED：按鈕目前為按下。

官方《Windows 介面應用程式設計指南》的六個按鈕樣式分別以下列 TBBS 值來表示︰

- 向上 = 0

- 滑鼠向下 = TBBS_PRESSED(&#124;任何其他样式)

- 停用 = TBBS_DISABLED

- 向下 = TBBS_CHECKED

- 已禁用 TBBS_CHECKED&#124;TBBS_DISABLED

- 不定 = TBBS_INDETERMINATE

## <a name="cdialogbar"></a><a name="_mfcnotes_cdialogbar"></a>CDialog 列

對話方塊列是包含標準 Windows 控制項的控制列。 它就像是一個包含控制項，並支援在這些控制項之間使用 Tab 鍵的對話方塊。 它也像是一個使用對話方塊範本來代表該列的對話方塊。

`CDialogBar` 可用於預覽列印工具列，其中包含標準按鈕控制項。

使用 `CDialogBar` 就像是使用 `CFormView`。 您必須定義對話方塊列的對話方塊範本，並移除 WS_CHILD 以外的所有樣式。 請注意，此對話方塊不能顯示。

`CDialogBar` 的控制項告知會傳送至控制列的父代 (就像是工具列按鈕)。

## <a name="ccmdui-support-for-cdialogbar"></a>CDialogBar 的 CCmdUI 支援

對話框欄按鈕應通過ON_UPDATE_COMMAND_UI處理程序機制進行更新。 在空閒時,對話方塊列將呼叫ON_UPDATE_COMMAND_UI處理程式,其中包含 ID >= 0x8000(即命令 ID 範圍內)的所有按鈕的命令 ID。

ON_UPDATE_COMMAND_UI處理程式可以呼叫:

- Enable：若要啟用或停用按鈕。

- SetText：若要變更按鈕的文字。

您可以透過標準視窗管理員 API 完成自訂。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
