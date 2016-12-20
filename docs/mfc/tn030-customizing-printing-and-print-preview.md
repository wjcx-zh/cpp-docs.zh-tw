---
title: "TN030：自訂列印和預覽列印 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.print"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自訂列印和預覽列印"
  - "預覽列印, 自訂"
  - "列印 [MFC], 檢視"
  - "列印檢視"
  - "TN030"
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN030：自訂列印和預覽列印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個附註描述自訂列印和預覽列印處理序並描述用於 `CView` 的回呼常式和回呼常式的用途和 **CPreviewView**的成員函式。  
  
## 問題  
 MFC 提供大部分列印提供完整的方案，並預覽列印需要。  在大部分情況下，需要一點程式碼能夠檢視列印和預覽。  然而，有需要大量的開發人員部分的最佳化方式列印，因此某些應用程式需要將特定使用者介面項目至預覽列印模式。  
  
## 有效的列印  
 當使用標準方法的 MFC 應用程式列印， Windows 會將所有繪圖裝置介面 \(Graphics Device \(GDI\) 輸出呼叫記憶體中繼檔。  當呼叫 `EndPage` 時， Windows 會播放一次中繼檔印表機需要列印一頁的每部實體群組列。  在轉換期間， GDI 經常查詢中止程序判斷它是否應該繼續。  通常會中止程序允許訊息處理列印對話方塊，讓使用者可以中止列印工作。  
  
 可惜的是，這可能會使得列印處理序。  如果在應用程式中列印必須比使用標準技術快速可以達成，您必須實作手動行帶效果。  
  
## 列印行帶效果  
 若要手動聯結，您必須如需實作列印迴圈沒有這種 `OnPrint` 呼叫每頁的多次 \(每次一個群組列\)。  列印迴圈在 viewprnt.cpp 的 **OnFilePrint** 函式實作。  在您的 `CView`衍生類別，您多載這個函式，以便處理的列印命令訊息對應項目呼叫您的列印功能。  複製 **OnFilePrint** 常式並變更列印迴圈加入至實作行帶效果。  您可能也會想要透過行帶效果矩形加入至列印功能，讓您可以最佳化根據列印頁面的部分的繪圖。  
  
 其次，您必須經常呼叫 `QueryAbort` ，則繪製群組列時。  否則，中止程序不會呼叫，而且使用者無法取消列印工作。  
  
## 預覽列印:與使用者介面的電子紙張  
 預覽列印，執行基本上，把顯示變更的嘗試印表機的模擬。  根據預設，主視窗的工作區用於完整顯示一個頁面在視窗內。  使用者可以放大的頁面區域詳細檢視。  對於其他支援，使用者在預覽模式甚至允許編輯文件。  
  
## 自訂預覽列印  
 這個附註只處理修改預覽列印的一個方面:將 UI 到預覽方式。  其他修改是可行的，不過，這類變更超出這個討論範圍。  
  
## 將 UI 到預覽方式  
  
1.  從 **CPreviewView**衍生的檢視類別。  
  
2.  將您想要的 UI 方面的命令處理常式。  
  
3.  如果您將視覺外觀以顯示，請覆寫 `OnDraw` 並在呼叫 **CPreviewView::OnDraw.**之後執行繪圖  
  
## OnFilePrintPreview  
 這是預覽列印命令的處理常式。  具有預設實作:  
  
```  
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
        delete pState;      // preview failed to initialize,   
                    // delete State now  
    }  
}  
```  
  
 **DoPrintPreview** 會隱藏應用程式的主要窗格。  控制列，例如狀態列，可以藉由指定它們保留在 pState\-\>**dwStates** 成員 \(這是位元遮罩，而個別的控制項中的位元是由 AFX\_IDW\_MYBAR \( **AFX\_CONTROLBAR\_MASK**\)\) 所定義。  Windows pState\-\>**nIDMainPane** 是將自動隱藏和 reshown 的視窗。  **DoPrintPreview** 會建立標準預覽的 UI 的按鈕列。  如果特殊 Windows 處理是必要的，例如隱藏或顯示其他視窗，應該執行，在 **DoPrintPreview** 呼叫之前。  
  
 根據預設，當預覽列印完成時，它會傳回控制列對它們的原始狀態和主要窗格為可見。  如果特殊處理，就需要在 **EndPrintPreview.**覆寫必須完成如果 **DoPrintPreview** 失敗，也請提供特殊處理。  
  
 DoPrintPreview 呼叫:  
  
-   對話方塊樣板資源 ID 的預覽工具列。  
  
-   對執行列印預覽列印的檢視指標。  
  
-   預覽檢視類別的執行階段類別。  這在 DoPrintPreview 將動態建立。  
  
-   CPrintPreviewState 指標。  請注意在框架*無法*建立 CPrintPreviewState 結構 \(或衍生的結構，如果應用程式需要儲存的詳細狀態\)。  DoPrintPreview 為非強制回應的，並將這個結構必須被回收，直到 EndPrintPreview 呼叫。  
  
    > [!NOTE]
    >  如果不同的檢視或檢視類別並不支援是必要的，應該將該物件的指標當做第二個參數。  
  
## EndPrintPreview  
 這個呼叫結束預覽列印模式。  移至在預覽列印最後顯示的文件的頁面通常是適當的。  **EndPrintPreview** 是應用程式的電腦會這樣做。  pInfo\-\>`m_nCurPage` 成員是最後一個顯示的頁面 \(最左邊，如果兩個頁面中顯示了\)，因此，指標是網頁上使用者是感興趣的提示有關。  因為應用程式檢視的結構不明的架構，您必須提供程式碼移至選取上的點。  
  
 您應該在呼叫 **CView::EndPrintPreview**之前執行大部分的動作。  這個呼叫反轉 **DoPrintPreview** 作用並刪除 pView、pDC 和 pInfo。  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC, pInfo, point, pView);  
```  
  
## CWinApp::OnFilePrintSetup  
 必須為列印設定功能表項目對應至這個。  在大部分情況下，覆寫實作是不必要的。  
  
## 頁面用語  
 其他問題是該網頁編號和順序。  對於簡單的文書處理器類型應用程式，這是簡單的問題。  大部分的預覽列印系統假設，每個列印頁面對應至文件中的頁面。  
  
 在嘗試提供通用的方案，您必須考慮的幾項工作。  試想一個電腦輔助設計系統。  使用者會涵蓋幾 E 大小工作表的繪圖。  在 E 大小 \(或較小，調整\) 繪圖機，網頁編號在簡單的案例。  但是，在雷射印表機，列印每張紙張大小 16 頁，預覽列印識別為何「Page」?  
  
 做為展示段落狀態，預覽列印如同印表機。  因此，使用者會看到哪些從選取的特定印表機出現。  它是由決定的檢視決定影像在每頁列印。  
  
 在 `CPrintInfo` 結構的頁面描述字串提供顯示頁碼方法給使用者，則可以表示為每個頁面的數字 \(「Page 1 」或「Page 1\-2」\)。這個字串是由 **CPreviewView::OnDisplayPageNumber**的預設實作使用。  如果不同的顯示，就需要一個可能會覆寫這個虛擬函式，例如， 「Sheet1，組件 A， B」。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)