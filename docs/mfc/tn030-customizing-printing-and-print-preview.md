---
title: TN030： 自訂列印和預覽列印 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.print
dev_langs:
- C++
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8331bbde9cf749d3b86b8970543d7a3b46be90fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381136"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030：自訂列印和預覽列印

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

本附註說明自訂列印和預覽列印的程序，並說明中所使用的回呼常式的目的`CView`回呼常式和成員函式和`CPreviewView`。

## <a name="the-problem"></a>問題

MFC 提供完整的解決方案，大部分的列印和預覽列印需要。 在大部分情況下，一些額外的程式碼是一定要有能夠列印和預覽的檢視。 不過，有最佳化方法列印需要極大的心力，讓開發人員執行，而且有些應用程式需要特定的使用者介面項目將預覽列印模式。

## <a name="efficient-printing"></a>有效率的列印

當 MFC 應用程式會列印使用標準的方法時，Windows 會導向至記憶體中中繼檔的所有圖形裝置介面 (GDI) 輸出呼叫。 當`EndPage`是呼叫，Windows 會播放一次是為每個實體群組列印表機列印一頁所需要的中繼檔。 這在呈現期間，GDI 經常查詢中止的程序，來判斷應該繼續。 通常在中止程序可讓訊息進行處理以供使用者可能會中止列印工作使用 [列印] 對話方塊。

不幸的是，這可能會降低列印程序。 如果您的應用程式中列印必須比可以使用標準的技術來達成更快，您必須實作手動矩形。

## <a name="print-banding"></a>列印矩形

若要以手動方式頻外，您必須重新實作列印迴圈，`OnPrint`多次呼叫每個頁面 （每一次頻外）。 列印迴圈中實作`OnFilePrint`viewprnt.cpp 中的函式。 在您`CView`-衍生的類別，以便處理的列印命令的訊息對應項目會呼叫您列印的函式多載這個函式。 複製`OnFilePrint`常式，並且將變更實作帶狀列印迴圈。 您可能會也想要傳遞至列印函式的條紋的矩形，以便您可以最佳化列印頁面的區段為基礎的繪圖。

第二，您必須經常呼叫`QueryAbort`繪製群組列時。 否則不會呼叫中止程序，而且使用者將無法取消列印工作。

## <a name="print-preview-electronic-paper-with-user-interface"></a>列印預覽： 具有使用者介面的電子文件

列印預覽中，在本質上，嘗試開啟顯示到模擬的印表機。 根據預設，用戶端主視窗的區域用來顯示完整視窗內的一或兩個頁面。 使用者就能夠放大網頁來查看更多詳細資料中的區域。 提供額外的支援，使用者甚至可以編輯 [預覽] 模式中的文件。

## <a name="customizing-print-preview"></a>自訂列印預覽

修改預覽列印的其中一個層面只處理這個附註： 新增的 UI，以預覽模式。 其他修改都有可能，但這類變更不在本文的討論範圍內。

## <a name="to-add-ui-to-the-preview-mode"></a>若要將 UI 加入至預覽模式

1. 衍生檢視類別從`CPreviewView`。

2. 新增您想要的 UI 層面的命令處理常式。

3. 如果您要新增視覺外觀的顯示，覆寫`OnDraw`，並執行之後呼叫繪圖`CPreviewView::OnDraw`。

## <a name="onfileprintpreview"></a>OnFilePrintPreview

這是預覽列印命令處理常式。 其預設實作是：

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` 將隱藏應用程式的主窗格。 控制列，例如 [狀態] 列中，可以保留 pState 中指定它們->*dwStates* （這是位元遮罩的位元和個別的控制列藉由 AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR) 所定義） 的成員。 -> 視窗 pState*nIDMainPane*是會自動隱藏並 reshown 的視窗。 `DoPrintPreview` 接著會建立一個按鈕列標準預覽 ui。 如果需要特殊的視窗處理，例如隱藏或顯示其他視窗，應該完成之前`DoPrintPreview`呼叫。

根據預設，當預覽列印完成時，它會傳回控制列至其原始狀態 」 和 「 主窗格為可見。 如果需要特殊處理，它應該是覆寫`EndPrintPreview`。 如果`DoPrintPreview`失敗，也會提供特殊處理。

呼叫 DoPrintPreview:

- [預覽] 工具列的對話方塊範本資源識別碼。

- 若要執行列印預覽列印檢視指標。

- 預覽檢視類別的執行階段類別。 這將 DoPrintPreview 中動態建立。

- CPrintPreviewState 的指標。 CPrintPreviewState 結構 （或應用程式需要保留的多個狀態的衍生的結構） 必須注意*不*框架上建立。 DoPrintPreview 為非強制回應和 EndPrintPreview 呼叫之前，必須存活下來這個結構。

  > [!NOTE]
  > 如果列印支援需要不同的檢視或檢視類別，該物件的指標應該傳遞為第二個參數。

## <a name="endprintpreview"></a>EndPrintPreview

這稱為終止預覽列印模式。 它通常會移到上一次預覽列印中顯示的文件中的頁面。 `EndPrintPreview` 是應用程式的機會，若要這麼做。 -> PInfo*m_nCurPage*成員是上次顯示 （最左邊的如果兩個頁面所顯示），頁面且指標位於提示，當做在其中的頁面上的使用者有興趣。 由於應用程式的檢視的結構是未知的 framework，您必須提供的程式碼，以移至所選的點。

您應該執行大部分的動作，然後再呼叫`CView::EndPrintPreview`。 這個呼叫會反轉的效果`DoPrintPreview`並刪除 pView，pDC 和 pInfo。

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup

這必須設定列印格式 功能表項目的對應。 在大部分情況下，不需要覆寫的實作。

## <a name="page-nomenclature"></a>頁面的專門用語

另一個問題是頁碼和順序。 簡單的文書處理器類型的應用程式，這是簡單的問題。 大部分的預覽列印系統會假設每個列印的頁面對應至文件中的某一個頁面。

在想要提供通用的解決方案，有一些事情需要考慮。 假設 CAD 系統。 使用者必須涵蓋數個電子大小的工作表的繪圖。 E 大小 （或較小，調整） 繪圖機，頁碼編排方式就是簡單的情況。 但雷射印表機，列印 16 的大小每一頁，考慮哪些因素會預覽列印 「 頁面 」

如簡介段落所述，例如印表機做預覽列印。 因此，使用者會看到什麼會送出特定選取的印表機。 這是由檢視表來判斷何種映像會列印每個頁面上。

中的頁面描述字串`CPrintInfo`結構提供方法來向使用者顯示的頁碼，如果它可以表示成每個頁面的一個數字 (如 「 第 1 頁 」 或 「 頁面 1-2")。 預設實作會使用此字串`CPreviewView::OnDisplayPageNumber`。 如果需要不同的顯示，使用者可能會覆寫此虛擬的函式，來提供，例如，"Sheet1 區段 A，B"。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
