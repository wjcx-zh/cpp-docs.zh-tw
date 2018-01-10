---
title: "TN030： 自訂列印和預覽列印 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.print
dev_langs: C++
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa11c30fb41630a5b293698fe3e69a80509f3f2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030：自訂列印和預覽列印
> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 此提示描述自訂列印和預覽列印的程序，並且描述中使用的回呼常式目的`CView`回呼常式和成員函式和**CPreviewView**。  
  
## <a name="the-problem"></a>問題  
 MFC 提供完整的解決方案，大部分的列印和預覽列印需要。 在大部分情況下，不使用其他程式碼是一定要有能夠列印和預覽的檢視。 不過，有最佳化的方式列印需要多加用心人員，而且有些應用程式需要將特定的使用者介面項目新增至 預覽列印模式。  
  
## <a name="efficient-printing"></a>有效率的列印  
 MFC 應用程式會列印使用標準方法，Windows 會指示記憶體中中繼檔的所有圖形裝置介面 (GDI) 輸出呼叫。 當`EndPage`是呼叫，Windows 會播放一次針對每個實體群組列印表機列印一頁所需的中繼檔。 這在呈現期間，GDI 經常查詢中止程序，以判斷應該繼續。 通常中止程序可讓訊息進行處理以供使用者可能會中止列印工作使用 [列印] 對話方塊。  
  
 不幸的是，這可能會降低列印程序。 如果您的應用程式中列印必須比可以使用標準的技術來達成，您必須實作手動矩形。  
  
## <a name="print-banding"></a>列印矩形  
 若要手動頻外，您必須重新實作列印迴圈，`OnPrint`多次呼叫每個分頁 （每個頻外）。 列印迴圈中實作**OnFilePrint** viewprnt.cpp 中的函式。 在您`CView`-衍生的類別，以便處理列印命令的訊息對應項目會呼叫您列印的函式多載這個函式。 複製**OnFilePrint**常式，並且將變更實作帶狀列印迴圈。 您也想要傳遞至您的列印函式的條紋矩形，讓您可以最佳化繪圖根據列印頁面的區段。  
  
 第二，您必須經常呼叫`QueryAbort`繪製頻外時。 否則不會呼叫中止程序，而且使用者將無法取消列印工作。  
  
## <a name="print-preview-electronic-paper-with-user-interface"></a>Print Preview： 使用者介面的電子文件  
 列印預覽，本質上而言，嘗試將轉換成模擬印表機的顯示。 根據預設，主視窗的工作區用來顯示完全在視窗內的一或兩頁。 使用者也可放大頁面，以查看更多詳細資料中的某個區域。 與其他支援，使用者可能甚至允許編輯預覽模式中的文件。  
  
## <a name="customizing-print-preview"></a>自訂列印預覽  
 修改預覽列印的其中一個層面只處理這個附註： 加入 UI，以預覽模式。 其他的修改可能會但這類變更不在本文的討論範圍內。  
  
## <a name="to-add-ui-to-the-preview-mode"></a>將 UI 加入預覽模式  
  
1.  衍生檢視類別從**CPreviewView**。  
  
2.  加入您想要的 UI 層面的命令處理常式。  
  
3.  如果您要將視覺外觀的顯示，覆寫`OnDraw`並執行之後呼叫繪圖**CPreviewView::OnDraw。**  
  
## <a name="onfileprintpreview"></a>OnFilePrintPreview  
 這是預覽列印命令處理常式。 其預設實作是：  
  
```  
void CView::OnFilePrintPreview()  
{ *// In derived classes,
    implement special window handling here *// Be sure to Unhook Frame Window close if hooked.  
 *// must not create this on the frame. Must outlive this function  
    CPrintPreviewState* pState = new CPrintPreviewState;  
 
    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR,
    this,  
    RUNTIME_CLASS(CPreviewView),
    pState))  
 { *// In derived classes,
    reverse special window handling *// here for Preview failure case  
 
    TRACE0("Error: DoPrintPreview failed");

    AfxMessageBox(AFX_IDP_COMMAND_FAILURE);

 delete pState;      // preview failed to initialize, *// delete State now  
 }  
}  
```  
  
 **DoPrintPreview**會隱藏主應用程式的窗格。 控制列，例如 [狀態] 列中，可以保留在 pState]-> [**dwStates**成員 (這是位元遮罩，以及個別控制列的位元會由**AFX_CONTROLBAR_MASK**(AFX_IDW_MYBAR))。 視窗 pState]-> [**nIDMainPane**是會自動隱藏並 reshown 的視窗。 **DoPrintPreview**接著會建立一個按鈕列的標準 Preview UI。 如果需要特殊的視窗處理，例如隱藏或顯示其他視窗之前應該完成**DoPrintPreview**呼叫。  
  
 根據預設，當預覽列印完成時，它會傳回控制列至其原始狀態和主要的窗格，即可顯示。 如果需要特殊處理，則應該執行中的覆寫**EndPrintPreview。** 如果**DoPrintPreview**失敗，也提供特殊處理。  
  
 呼叫 DoPrintPreview 時所使用：  
  
-   [預覽] 工具列的對話方塊範本資源識別碼。  
  
-   若要執行列印預覽列印檢視指標。  
  
-   預覽檢視類別的執行階段類別。 這將 DoPrintPreview 中動態建立。  
  
-   CPrintPreviewState 指標。 CPrintPreviewState 結構 （或衍生的結構，如果應用程式需要保留的多個狀態） 必須注意*不*框架上建立。 DoPrintPreview 為非強制回應，而且此結構必須存留 EndPrintPreview 呼叫之前。  
  
    > [!NOTE]
    >  如果列印支援需要不同的檢視或檢視類別，應該做為第二個參數傳遞給該物件的指標。  
  
## <a name="endprintpreview"></a>EndPrintPreview  
 這稱為結束預覽列印模式。 它通常會移至上次在預覽列印中顯示的文件中的頁面。 **EndPrintPreview**執行此作業的應用程式的機會。 PInfo]-> [`m_nCurPage`成員是上次顯示 （最左邊的如果兩個頁面時顯示），頁面且指標位於提示，當做在頁面上使用者已有興趣。 因為未知的 framework 的應用程式檢視的結構，您必須提供程式碼以移至所選的點。  
  
 您應該執行大部分的動作，然後再呼叫**CView::EndPrintPreview**。 此呼叫會反轉的效果**DoPrintPreview**並刪除 pView、 pDC 和 pInfo。  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC,
    pInfo,
    point,
    pView);
```  
  
## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 這必須設定列印格式 功能表項目的對應。 在大部分情況下，不需要覆寫的實作。  
  
## <a name="page-nomenclature"></a>頁面術語表  
 另一個問題是頁碼和順序。 簡單的文書處理器類型的應用程式，這是簡單的問題。 大多數的預覽列印系統會假設每個列印的頁面對應至文件中的一個頁面。  
  
 在想要提供通用的方案，有幾件事，請考慮。 假設 CAD 系統。 使用者必須涵蓋數個電子大小的工作表的繪圖。 E 大小 （或更小，調整） 繪圖機，頁碼編排方式會如同在簡單案例。 但雷射印表機、 列印 16 A 大小每一頁，並預覽列印考慮 「 頁面 」  
  
 介紹段落所述，當預覽列印 會有如印表機。 因此，使用者會看到什麼會送出的特定的印表機上已選取。 這是由檢視表來判斷哪些映像會列印每個頁面上。  
  
 中的頁面描述字串`CPrintInfo`結構會提供一種向使用者顯示的頁碼，如果它可以表示成每個頁面的一個數字 (如同 「 第 1 頁 」 或 「 頁 1-2")。 這個字串由的預設實作**CPreviewView::OnDisplayPageNumber**。 如果需要不同的顯示，其中可能會覆寫此虛擬函式，以提供，例如，"Sheet1 區段 A、 B"。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

