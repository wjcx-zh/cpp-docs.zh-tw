---
title: "CMFCEditBrowseCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCEditBrowseCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCEditBrowseCtrl class"
  - "CMFCEditBrowseCtrl constructor"
  - "CMFCEditBrowseCtrl::PreTranslateMessage method"
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCEditBrowseCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCEditBrowseCtrl` 類別支援編輯瀏覽控制項，是可編輯的文字方塊中選擇性地包含瀏覽按鈕。   當使用者按一下 \[瀏覽\] 按鈕時，控制項會執行自訂動作或顯示包含檔案瀏覽器或資料夾瀏覽器的標準的對話方塊。  
  
## 語法  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|預設建構函式。|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md)|啟用或停用 \(隱藏\) 的瀏覽按鈕。|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFileBrowseButton.md)|在檔案 *瀏覽模式* 啟用瀏覽按鈕並將編輯瀏覽控制項。|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFolderBrowseButton.md)|在 *資料夾瀏覽模式* 啟用瀏覽按鈕並將編輯瀏覽控制項。|  
|[CMFCEditBrowseCtrl::GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md)|傳回目前瀏覽模式。|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](../Topic/CMFCEditBrowseCtrl::OnAfterUpdate.md)|呼叫由架構，在編輯瀏覽控制項更新瀏覽動作後的結果。|  
|[CMFCEditBrowseCtrl::OnBrowse](../Topic/CMFCEditBrowseCtrl::OnBrowse.md)|呼叫由架構之後在使用者按一下 \[瀏覽\] 按鈕。|  
|[CMFCEditBrowseCtrl::OnChangeLayout](../Topic/CMFCEditBrowseCtrl::OnChangeLayout.md)|重新繪製目前編輯瀏覽控制項。|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](../Topic/CMFCEditBrowseCtrl::OnDrawBrowseButton.md)|呼叫框架的瀏覽按鈕。|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](../Topic/CMFCEditBrowseCtrl::OnIllegalFileName.md)|呼叫框架，則是不合法的檔名是編輯控制項中輸入。|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  如需語法的詳細資訊，請參閱 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](../Topic/CMFCEditBrowseCtrl::SetBrowseButtonImage.md)|將瀏覽按鈕的自訂影像。|  
  
## 備註  
 使用編輯瀏覽控制項選取檔案或資料夾名稱。  或者，請使用控制項執行自訂動作 \(例如顯示對話方塊。  您可以顯示或不顯示瀏覽按鈕，然後，您可以將自訂標籤或影像按鈕。  
  
 編輯瀏覽控制項的 *瀏覽模式* 決定是否顯示瀏覽按鈕，以及哪些動作，當按一下按鈕時。    如需詳細資訊，請參閱 [GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md) 方法。  
  
 `CMFCEditBrowseCtrl` 類別支援下列方法。  
  
 `custom mode`  
 當使用者按一下 \[瀏覽\] 按鈕時，自訂動作。  例如，您可以顯示特定應用程式的對話方塊。  
  
 `file mode`  
 當使用者按一下 \[瀏覽\] 按鈕時，會將標準資料夾選取對話方塊隨即顯示。  
  
 `folder mode`  
 當使用者按一下 \[瀏覽\] 按鈕時，標準資料夾選取對話方塊隨即顯示。  
  
## HOW TO:指定編譯瀏覽控制項  
 執行下列步驟來合併在應用程式中編輯瀏覽控制項:  
  
1.  如果您要實作自訂瀏覽模式， `CMFCEditBrowseCtrl` 從類別衍生您的類別會覆寫 [CMFCEditBrowseCtrl::OnBrowse](../Topic/CMFCEditBrowseCtrl::OnBrowse.md) 方法。   在覆寫的方法，執行自訂動作瀏覽並更新具有所產生的編譯瀏覽控制項。  
  
2.  內嵌 `CMFCEditBrowseCtrl` 物件或衍生自的編輯瀏覽控制項物件至父視窗物件。  
  
3.  如果您使用 \[**類別精靈**\] 建立對話方塊，請將編輯控制項 \(`CEdit`\) 加入至對話方塊表單。   此外，請將變數存取在標頭檔中的控制項。   在標頭檔中，從 `CEdit` 變更引數的型別轉換為 `CMFCEditBrowseCtrl`。   編輯瀏覽控制項就會自動建立。   如果您不使用 \[**類別精靈**\]，請將 `CMFCEditBrowseCtrl` 變數加入至標頭檔 `Create` 再呼叫其方法。  
  
4.  如果您將編輯瀏覽控制項加入至對話方塊，請使用 \[**ClassWizard**\] 工具設定資料交換。  
  
5.  呼叫 [EnableFolderBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFolderBrowseButton.md)、 [EnableFileBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableFileBrowseButton.md)或 [EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md) 方法設定瀏覽模式和顯示瀏覽按鈕。    呼叫 [GetMode](../Topic/CMFCEditBrowseCtrl::GetMode.md) 方法取得目前瀏覽模式。  
  
6.  用來瀏覽按鈕想要提供自訂影像，請呼叫方法 [SetBrowseButtonImage](../Topic/CMFCEditBrowseCtrl::SetBrowseButtonImage.md) 或覆寫 [OnDrawBrowseButton](../Topic/CMFCEditBrowseCtrl::OnDrawBrowseButton.md) 方法。  
  
7.  從編輯瀏覽控制項要移除瀏覽按鈕，便會使用 `bEnable` 參數的 [EnableBrowseButton](../Topic/CMFCEditBrowseCtrl::EnableBrowseButton.md) 方法設定為 `FALSE`。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## 範例  
 下列範例會在 `CMFCEditBrowseCtrl` 類別會示範如何使用兩個方法: `EnableFolderBrowseButton` 和 `EnableFileBrowseButton`。   這個範例是 [新的控制項範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!CODE [NVC_MFC_NewControls#6](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#6)]  
[!CODE [NVC_MFC_NewControls#7](../CodeSnippet/VS_Snippets_Misc/NVC_MFC_NewControls#7)]  
  
## 需求  
 **標題:** afxeditbrowsectrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)